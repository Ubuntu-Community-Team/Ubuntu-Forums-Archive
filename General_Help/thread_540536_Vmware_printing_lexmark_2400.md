---
title: "Vmware printing lexmark 2400"
date: 2007-09-01
forum: General Help
---

### Post by Weyoun on 2007-09-01
Hello! I'm new to ubuntu. Using it for about 2 months! so take it easy on me
I have lexmark 2400 series wich doesn't work, so i installed Vmware server and winXP on it and then I installed printer on that windows and everything works perfect but i want to print trough the virtual machine, I don't want to use windows for that. For example, I want to print a document, I have to type it in virtual machine and then print it in, I don't want that, I want to do jobs in Kubuntu (I use Kubuntu)and use evil OS (winXP) ONLY as a path to my Lexmark. Is it possible to make virtual machine something like network computer or something like that! can you please be precise in explanation
Thanks so much!!![

---

### Post by wolfen69 on 2007-09-01
i don't think you can set up a network on the same computer. you may have to use the "evil OS" for printing.

---

### Post by gimplar on 2007-10-14
I'm pretty sure you can do this by setting up a virtual network within your computer. I'm not really sure how to do this in VMWare-player but I know it's possible. 

Once you get this working you just share your printer in WinXP and you can then network print your documents from Ubuntu.

Downside of this is that your virtual machine will have to be up and running everytime you want to print.

You may be able to circumvent the entire need of setting up a intra-host network and just share the printer and print over your local network. It'd be kinda silly, the print data would go to your router and route right back into the same computer. Really inefficient but if your network is small it shouldn't really affect anything.

Good luck with that though! (I'm new to Linux as well, only my 2nd week of using Ubuntu)

---

