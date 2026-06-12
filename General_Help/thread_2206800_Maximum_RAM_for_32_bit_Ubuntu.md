---
title: "Maximum RAM for 32 bit Ubuntu"
date: 2014-02-20
forum: General Help
---

### Post by borgward on 2014-02-20
What is the maximum RAM for Ubuntu on 32 bit machine?

Plese don't tell me to get 64 bit machine umless you are going to give me one. I am stuck with 32 bit machine, so please stick to the question.

---

### Post by kostkon on 2014-02-20
The kernel is PAE enabled so the limit is very large, 64GB at the moment. More about PAE, [here]("http://en.wikipedia.org/wiki/Physical_Address_Extension").

If your CPU is one of those old Pentium Ms that don't support it then you are out of luck basically, you'll be limited to ~4GB

---

### Post by borgward on 2014-02-21
Thanks. The processor is 80547, PENTIUM 4 PRESCOTT DT..., 531, LGA, G1, ALTERNATE. I'm guessing that is not Pentium M.

---

### Post by kostkon on 2014-02-21
> **borgward said:**
> Thanks. The processor is 80547, PENTIUM 4 PRESCOTT DT..., 531, LGA, G1, ALTERNATE. I'm guessing that is not Pentium M.
You should be fine.

---

### Post by Yellow Pasque on 2014-02-22
The more pertinent question is. "How much RAM does the motherboard support?"

---

### Post by kostkon on 2014-02-22
> **borgward said:**
> Thanks. The processor is 80547, PENTIUM 4 PRESCOTT DT..., 531, LGA, G1, ALTERNATE. I'm guessing that is not Pentium M.
Hmm, if [that is your processor]("http://ark.intel.com/products/27465/Intel-Pentium-4-Processor-531-supporting-HT-Technology-1M-Cache-3_00-GHz-800-MHz-FSB"), then it's 64bit.

---

### Post by sanderj on 2014-02-22
> **Temüjin said:**
> The more pertinent question is. "How much RAM does the motherboard support?"

+1

Old mobo's don't go above 3 or 4 GB, and/or don't know memory hoisting.

---

### Post by david98 on 2014-02-22
> **Temüjin said:**
> The more pertinent question is. "How much RAM does the motherboard support?"


+1

---

