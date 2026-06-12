---
title: "Complete noob"
date: 2008-05-03
forum: General Help
---

### Post by avgazn on 2008-05-03
Hello i am a uber noob and I have 7.10 gutsy. I have a couple questions so please bear with me.I bave a triple boot of XP,Vista, and Ubuntu

1. Is it possible to uninstall grub but still launch ubunbu?

2. How can I do it?

3. Why is it that if i use a program like eawsybcd to add ubuntu to the boot manager it can't be opened?

4. Where can i download binfmt-support? 

5. Is it possible to have all three OS's on one screen instaeed of goign through menus? 

6. Where can i find ubuntu.bin?

7. what does ```
sudo dd if=/dev/hda of=/media/share/ubuntu.bin bs=512 count=1
```

```
hexdump -c/media/share/ubuntu.bin
```
mean?

8. How do you edit grub references to change boot time and etc?

If you read this thank you. Please help me

---

### Post by ghost_ryder35 on 2008-05-03
> **avgazn said:**
> Hello i am a uber noob and I have 7.10 gutsy. I have a couple questions so please bear with me.I bave a triple boot of XP,Vista, and Ubuntu
 
1. Is it possible to uninstall grub but still launch ubunbu?
 
2. How can I do it?
 
3. Why is it that if i use a program like eawsybcd to add ubuntu to the boot manager it can't be opened?
 
4. Where can i download binfmt-support? 
 
5. Is it possible to have all three OS's on one screen instaeed of goign through menus? 
 
6. Where can i find ubuntu.bin?
 
7. what does ```
sudo dd if=/dev/hda of=/media/share/ubuntu.bin bs=512 count=1
```
 
```
hexdump -c/media/share/ubuntu.bin
```
mean?
 
8. How do you edit grub references to change boot time and etc?
 
If you read this thank you. Please help me
1 and 2. [http://www.linuxdevcenter.com/pub/a/linux/2006/05/08/dual-boot-laptop.html?page=3](http://www.linuxdevcenter.com/pub/a/linux/2006/05/08/dual-boot-laptop.html?page=3)
3. idk
4. idk 
5. what do you mean?  run all three os's at once?  You could virtualize them and it would work.
6. idk
7.first line makes a file containing your boot sector of your linux drive
8. ```
 sudo gedit /boot/grub/menu.lst

```

---

### Post by Monicker on 2008-05-03
4) You can install binfmt-support from Synaptic or by using "sudo apt-get install binfmt-support" from a terminal session.

---

### Post by pbpersson on 2008-05-03
> **avgazn said:**
> Hello i am a uber noob and I have 7.10 gutsy. I have a couple questions so please bear with me.I bave a triple boot of XP,Vista, and Ubuntu

1. Is it possible to uninstall grub but still launch ubunbu?

2. How can I do it?

3. Why is it that if i use a program like eawsybcd to add ubuntu to the boot manager it can't be opened?

4. Where can i download binfmt-support? 

5. Is it possible to have all three OS's on one screen instaeed of goign through menus? 

6. Where can i find ubuntu.bin?

7. what does ```
sudo dd if=/dev/hda of=/media/share/ubuntu.bin bs=512 count=1
```

```
hexdump -c/media/share/ubuntu.bin
```
mean?

8. How do you edit grub references to change boot time and etc?

If you read this thank you. Please help me

6.  I do not have a file called ubuntu.bin on my machine but I did a Google search and it said something about it being created on another partition if you are setting up some dual boot environment

7.  If you want to view more information on a utility such as dd you can type "man dd" in a console prompt and get pages of information on what the if, of, and bs command-line switches do to modify the command.

---

### Post by ghost_ryder35 on 2008-05-03
> **pbpersson said:**
> 6. I do not have a file called ubuntu.bin on my machine but I did a Google search and it said something about it being created on another partition if you are setting up some dual boot environment
 
7. **If you want to view more information on a utility such as dd you can type "man dd"** in a console prompt and get pages of information on what the if, of, and bs command-line switches do to modify the command.
nice call :)

---

### Post by avgazn on 2008-05-03
> **ghost_ryder35 said:**
> 1 and 2. [http://www.linuxdevcenter.com/pub/a/linux/2006/05/08/dual-boot-laptop.html?page=3](http://www.linuxdevcenter.com/pub/a/linux/2006/05/08/dual-boot-laptop.html?page=3)
3. idk
4. idk 
5. what do you mean?  run all three os's at once?  You could virtualize them and it would work.
6. idk
7.first line makes a file containing your boot sector of your linux drive
8. ```
 sudo gedit /boot/grub/menu.lst

```

I mean the boot screen. Instead of starting up your comupter and clicking down to the windows choices can you put windows xp, vista, and ubuntu on one boot screen not going through menus

Can you explain which parts mean which so i can edit it to my computer setings.

---

### Post by avgazn on 2008-05-03
> **Monicker said:**
> 4) You can install binfmt-support from Synaptic or by using "sudo apt-get install binfmt-support" from a terminal session.

I have no internet.

---

### Post by avgazn on 2008-05-04
I'm sorry for the crazy triple post but what is a MBR? and when im instaling ubuntu how do i not install grub to the MBR? ```
http://www.scotthofer.com/How%20to%20triple%20boot%20XP%20Vista%20Linux.html
```

Also I have tried before to add ubuntu to the vista boot manager but it doesnt owrk.

---

### Post by virtuallinux on 2008-05-04
Ok, on the no internet thing, if you have access to another machine with internet, go to [packages.ubuntu.com]("http://packages.ubuntu.com"), scroll to the bottom of the page, and search for "binfmt-support". You can download the files from there and move them to your other machine.

---

### Post by avgazn on 2008-05-04
> **virtuallinux said:**
> Ok, on the no internet thing, if you have access to another machine with internet, go to [packages.ubuntu.com]("http://packages.ubuntu.com"), scroll to the bottom of the page, and search for "binfmt-support". You can download the files from there and move them to your other machine.

Thank you I'll try it and report back :)

Still need to know MBR and how not to install grub to it.

---

### Post by avgazn on 2008-05-06
> **virtuallinux said:**
> Ok, on the no internet thing, if you have access to another machine with internet, go to [packages.ubuntu.com]("http://packages.ubuntu.com"), scroll to the bottom of the page, and search for "binfmt-support". You can download the files from there and move them to your other machine.

I downloaded it but how do you install it? im a super noob. I unpacked it. now what? also i think the version is for hardy is there any for gutsy? and what is universe?

---

### Post by virtuallinux on 2008-05-06
there should be an option when you're configuring the search where you can choose which version you're searching for.  As far as installation, I think you must have chosen the wrong download. What you should have is a .deb package, which you can basically just double click to install.  Look at the bottom of [_this page_]("http://packages.ubuntu.com/gutsy/binfmt-support") and choose the "all" option under architectures.

---

