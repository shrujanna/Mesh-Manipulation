# 10-Layer Volumetric Cloth Simulation

A browser-based **cloth physics simulator** featuring **10 stacked layers**, depth-based colouring, realistic constraints, plastic deformation, and **line-based cutting**.

Built entirely using HTML5 Canvas + Vanilla JavaScript.  

---

## Features

- **10 volumetric layers** with depth shading  
- **Structural, shear, and inter-layer constraints**  
- **Plastic deformation** & stretching  
- **Interactive controls**
  - Left-click drag → Pull / deform cloth  
  - Right-click drag → Slice the cloth with a drawn line  
- **Dynamic parameters**
  - Cloth density (spacing)  
  - Gravity strength  
- **Rainbow layer visualization** for clarity and aesthetics

---

## How to Run Locally

1. Download or clone this repository.
2. Ensure the project contains the main HTML file.
3. Open the HTML file in any modern browser:
   - Double click the file, or  
   - Right-click → *Open With* → your browser (Chrome, Firefox, Safari)

> ⚠ No dependencies. No install step. Everything runs client-side inside the browser.

---

## Controls

| Action | Input |
|--------|--------|
| **Pull cloth / deform** | Left-click + drag |
| **Cut using a line** | Right-click + drag |
| **Reset simulation** | *Reset Cloth* button |
| **Change cloth spacing (density)** | Spacing slider |
| **Adjust gravity** | Gravity slider |

---

## 🔧 Technical Overview (Short Version)

### **Points (Vertices)**  
Each cloth point stores:
- `x, y` position and previous position (for Verlet integration)  
- Layer index (`z`)  
- Pinned state  
- Update loop applying gravity, drag, boundary constraints  

### **Constraints**
Three types of links maintain cloth structure:

1. **Structural constraints**  
   - Horizontal and vertical threads

2. **Shear constraints**  
   - Diagonal stabilizers

3. **Layer constraints**  
   - Binds the 10 layers together for thickness

Each constraint:
- Maintains a **rest length**
- Applies **stiffness**
- Allows **plastic stretching**
- Tears when overstretched

### **Tearing System**
- Right-click line drawing checks intersections with constraints  
- Overstrained constraints tear dynamically  
- Vertex splitting prevents collapsing mesh when multiple tears occur

### **Rendering**
- Cloth drawn from **back (z = 9)** to **front (z = 0)**  
- Each layer has a distinct RGB colour  
- Depth darkens colour for pseudo-volumetric feel

---

## Notes

- Uses **Verlet integration** for stable cloth motion.  
- Increasing spacing reduces resolution but improves performance.  
- Inter-layer constraints are what give the cloth its “thickness.”  
- Cutting + plastic deformation combined create realistic tearing effects.

---

## Demo Video Link
https://drive.google.com/file/d/1p7wYUoerb4_4XTUSgavJFAVfJjmj-QnF/view?usp=share_link


