# CustomSIREN
This repository explores a smooth, bounded periodic activation function for SIREN architectures, designed to preserve infinite differentiability while improving numerical stability through controlled amplitude clipping.
# Custom Activation Function for SIREN Networks

This repository investigates a modified activation function for **SIREN (Sinusoidal Representation Networks)** that preserves periodic structure while introducing bounded behavior to improve stability. The project evaluates the behavior of the custom activation both analytically and empirically on image fitting tasks.

---

## 📌 Background

SIREN networks use sinusoidal activation functions to model high-frequency signals and continuous implicit representations. While sine activations provide excellent representational capacity, they can suffer from large activation magnitudes that may negatively affect training stability.

To address this, this work proposes a **smooth, bounded periodic activation function** that retains the core properties of SIREN while clipping extreme values.

---

## 🧠 Proposed Activation Function

### Custom Activation Function

The custom activation function is defined as:

**f(x) = tanh(γ · sin(βx))**, where **γ > 0** and **β > 0**

Its derivative is:

**f′(x) = γβ · cos(βx) · sech²(γ · sin(βx))**


### Key Properties
- **Infinitely differentiable**
- **Periodic structure inherited from sine**
- **Bounded output via tanh**
- **Continuous gradients**, consistent with SIREN design principles

---

## 📈 Activation Analysis

The activation function was analyzed by varying:
- **Frequency scaling**: \(\beta \in [0.5, 5]\)
- **Amplitude scaling**: \(\gamma \in [0.5, 5]\)

Comparisons between:
- `sin(x)`
- `tanh(sin(x))`

show that the proposed activation maintains periodicity while progressively clipping extreme values, potentially improving numerical stability without sacrificing expressive power.

---

## 🖼️ Image Fitting Experiment

The custom activation was integrated into a SIREN-style architecture and evaluated on a single image fitting task.

### Results
| Model | Final Loss |
|------|-----------|
| **Original SIREN (sin activation)** | 0.005613 |
| **Custom SIREN (tanh–sin activation)** | 0.006435 |

Both models successfully fit the target image within 100 epochs, with the custom activation achieving comparable performance while enforcing bounded activations.

---

## 🔬 Observations

- The proposed activation preserves SIREN’s ability to represent high-frequency details.
- Output clipping via `tanh` limits extreme activation values.
- Performance remains competitive with standard sinusoidal SIREN.
- The approach offers a potential trade-off between expressiveness and stability.

---

## 🧪 Code Structure

- `siren.ipynb`  
  - Activation function definition
  - Derivative verification
  - Activation plots for different γ and β
  - SIREN image fitting experiment
  - Loss comparison with standard SIREN

---

## 🚀 Future Work

- Extend experiments to larger datasets and 3D signals
- Study convergence behavior and gradient statistics
- Explore learnable γ and β parameters
- Apply the activation to audio, NeRFs, or PDE solving tasks

---

## 📚 References

- Sitzmann et al., *Implicit Neural Representations with Periodic Activation Functions (SIREN)*  
- PyTorch Documentation  

---

## ✨ Author

**Zarin Musarrat Manita**  
Graduate Student, Computer Engineering  
Arizona State University

---

