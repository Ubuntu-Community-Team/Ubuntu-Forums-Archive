---
title: "IDE Drive Setup"
date: 2007-11-14
forum: General Help
---

### Post by DCM36 on 2007-11-14
I'm about to install Ubuntu 7.10 and create a software RAID 0, and I was wondering which setup of my IDE drives would give me the optimum disk bandwidth.

Current Setup:

Primary Master: 80 GB HD1
Primary Slave: 80 GB HD2
Secondary Master: DVD Burner
Secondary Slave: CD Burner

From my understanding of IDE channels and such, I think that I would achieve the optimum performance by making the hard drives the masters on each channel and the optical drives slaves (as diagrammed below). Could anyone confirm this?

Proposed Setup:
Primary Master: 80 GB HD1
Primary Slave: DVD Burner
Secondary Master: 80 GB HD2
Secondary Slave: CD Burner

---

### Post by pdaigneault on 2007-11-14
I think its best to put all OS on Primary Master/Slave and optical drive on Secondary master/slave in an IDE setup. That way your  optical wont slow your hard drives down at all. SATA is a different config and you dont have master slave or any bandwidth limits per drive.

---

