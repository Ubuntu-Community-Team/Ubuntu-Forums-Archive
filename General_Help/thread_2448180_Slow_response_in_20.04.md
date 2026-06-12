---
title: "Slow response in 20.04"
date: 2020-08-03
forum: General Help
---

### Post by mbuhmann on 2020-08-03
I did a fresh install of Ubuntu 20.04 Desktop on a Dell Precision Tower 5810. It has an Intel Xeon 3.5Ghz, 16GB RAM, and an nVidia N310. It was configured as a RAID but I removed the RAID card and set the drives up as AHCI in the BIOS. Previously I had Linux Mint 18.1 installed and it worked fine, and then I went to openmediavault which is based on Debian. I'm primarily set up for the digital asset management system Resourcespace and shared storage for video and photo editing. Until moving to Ubuntu 20.04 everything was fine, but once I installed it things got very slow. Ex: when importing a 1GB SQL database via terminal it took nearly an hour whereas previously it only took a few minutes. And when I had only a couple windows open on the desktop it became unbearably slow with Firefox or Ubuntu Software or other windows taking nearly a min. to open or respond.

Does anyone have any suggestions in troubleshooting what the problem is? I would think my the workstation is powerful enough to handle the OS.

Thank you.

---

### Post by daniewicz on 2020-08-03
Does the System Monitor offer any insight?

---

### Post by mbuhmann on 2020-08-04
> **daniewicz said:**
> Does the System Monitor offer any insight?

I'll take a look when I'm in the office on Thurs. I can remote into my Windows system and then ssh via Putty into the command prompt. Is there a good command line option?

---

### Post by Impavidus on 2020-08-04
top or htop provide the same information as the system monitor and run in terminal, so can be used over ssh.

---

