---
title: "File transfer keeps failing inside VM"
date: 2018-08-10
forum: General Help
---

### Post by dbellecy on 2018-08-10
Because I am new to linux I am using USB sticks to transfer data from my computer to the VM on that computer. Problem is the it keeps failing at multiple different points in the transfer. Each time it fails it stops recognizing the USB, and it has done this with several different USB sticks. I didn't think this would be so hard.

---

### Post by HermanAB on 2018-08-10
Hmm, so do the transfer through the network, or copy the data to the host first, then to the VM...

Anyway, without telling us which kind of VM you are using on which kind of system, there isn't much we can do to help.

---

### Post by &amp;KyT$0P# on 2018-08-10
> **dbellecy said:**
> I am using USB sticks to transfer data from my computer to the VM on that computer.
Why are you doing it this way?
Does your VM program not have any type of "shared folders" that would work for your case?

---

### Post by dbellecy on 2018-08-10
I am very new to linux. I am just trying to figure out why I am having problems. I am sorry I didn't provide enough data. I got it to work by reformatting a USB stick and trying the whole process over. I still need to learn how to network my linux machines so I can send data much easier, but the internet didn't seem to have an answer that wasn't going to take longer than other just getting the USB to work.

---

### Post by SeijiSensei on 2018-08-10
What virtual machine software are using? If it's VirtualBox, you can use "shared folders" to make a directory on the host available to the guest. You need to install the Extension Pack to make this work. See [https://www.virtualbox.org/manual/ch04.html#sharedfolders](https://www.virtualbox.org/manual/ch04.html#sharedfolders) for details.

---

