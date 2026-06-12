---
title: "WRT54G linksys router quit working slightly after Gutsy install."
date: 2007-12-27
forum: General Help
---

### Post by dnbozss on 2007-12-27
My router worked fine for years until recently. I put Ubuntu Gutsy Gibbon on it. For the first week or so, it worked fine in Windows (the internet didn't work in Gibbon at first) but now it stopped. I don't know if the Ubuntu factor is the problem, all I know is that it is the only thing that mostly changed in the last few years (this is my first time dual booting.) But actually when it really stopped working, (which was while the computer was on, in Windows) was when I installed software for my Epson Perfection 3170 Photo scanner. Literally right as I ran the Smart Panel for it, the internet just shut off. When I plug the modem directly into the computer (as I am doing now), it works, so I know it must be the router. I system restored to before I installed the scanner software, and no luck, then I undid the restore. I reset the router both from the button on the back, and from my web browser numerous times. Still nothing. Then I tried switching to my old router, the BEFW11S4, and it actually stopped working as well. The one thing I did notice was that when I do ipconfig/all in the command line in both, when I am directly connected, it shows a "DNS suffix search list" being "hsd1.co.comcast", and "Connection-specific DNS suffix" being the same, whereas when I try the command while connected to the router, the first is not even present, and the latter is empty. Thanks for the help in advance, if there's any other details that might help, let me know.

I know I'm not using Ubuntu for the main part, but I'm fairly sure that it's the router, and not the PC, but I could be wrong. What I'm asking here is could this be Gutsy's fault?


*EDIT* SOLVED! I just cloned my PC's MAC address and it started working.....as usual, it wasn't Ubuntu's fault.

---

