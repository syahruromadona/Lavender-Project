
<img width="1024" height="688" alt="Lavender Banana (Compressed)" src="https://github.com/user-attachments/assets/ee57c857-786e-43f3-949e-97dcd580a1f3" />

Hasny Furniture is a leading custom kitchen furniture manufacturer in Perak, having won multiple awards such as the TVET Entrepreneur Award from MARA Perak and finalist in Anugerah Usahawan Aura Manjung 2025 – Pembuatan category. Lavender Project aims to solve the high-cost and time-consuming process of creating beautiful client-ready renderings of client’s kitchen furniture before manufacturing begins.

The project focused on optimizing an **in-house AI image generation pipeline** built around **ComfyUI** for a client-facing service. The original process was expensive and slow: each client deliverable cost approximately **RM800** to produce and took about **1 week** from request to completion. The core goal was to achieve a dramatic 100x cost reduction (targeting ~**RM8 per client** or equivalent), slash turnaround time to ~**1 day**, while strictly keeping the entire operation **in-house** to maintain full control and customization flexibility.

# Key Challenge

The primary bottleneck was the **lack of powerful local GPUs** capable of running complex, high-resolution ComfyUI workflows efficiently. On-premises hardware simply couldn't handle the compute demands at scale or speed, leading to long queue times, high manual oversight, and inflated per-client costs (driven largely by time/labor and inefficient resource use).

# Approach and Decision-Making

- Initially considered renting general-purpose cloud GPUs (e.g., via **RunPod**), which offer flexible, high-performance instances.
- However, most traditional cloud GPU providers charge **by the hour** (or per minute), including **idle time**, meaning costs accumulate even during workflow setup, model loading, testing, debugging, or waiting between client This would have eroded much of the intended cost savings, especially for variable or bursty workloads.
- After researching alternatives, shifted to **ComfyUI's own cloud service** (Comfy Cloud), which uses a **usage-based model** that charges **only for active GPU runtime** during actual workflow execution.
    - No billing occurs for **idle periods**, workflow editing, model downloads/uploads, or build/setup time.
    - This per-run pricing aligned perfectly with the need to minimize waste and pay strictly proportional to productive output.
- The switch enabled running demanding workflows on powerful remote GPUs without ongoing idle penalties, while still treating the service as an **in-house extension** (full control over ComfyUI workflows, custom nodes, prompts, and post-processing steps remained internal).

# Results and Impact

- **Cost per client** dropped dramatically, achieving the target range of ~**RM8** (or better) per deliverable through efficient GPU-second consumption and elimination of idle
- **Turnaround time** improved from ~1 week to ~**1 day** (often faster), thanks to

near-instant access to high-end GPUs, reduced queuing, and streamlined execution without local hardware limitations.

- The process stayed fully **in-house** in terms of creative control, IP, client data handling, and workflow ownership, only the raw compute was offloaded

# Key Learnings

1. **Always research and compare multiple service options thoroughly**, what appears to be the obvious choice (e.g., popular GPU rental platforms like RunPod) may carry hidden costs (idle billing) that undermine Surveying specialized tools tailored to your exact stack (here, ComfyUI-native cloud) can reveal far better economics.
2. **Seek client feedback as early as possible**, assumptions about what aspects "matter most" (e.g., ultra-fine control vs. speed/cost) can be wrong. Rapid iteration based on real user input ensured the optimization delivered value where it
3. **Resource constraints (like lacking powerful local GPUs) are not inherently negative**, they often force creative problem-solving, cost discipline, and exploration of smarter architectures. This is a very common situation across many teams and companies; turning it into an advantage through cloud augmentation is a repeatable
