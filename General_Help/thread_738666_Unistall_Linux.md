---
title: "Unistall Linux"
date: 2008-03-28
forum: General Help
---

### Post by GuhPuick on 2008-03-28
I have a single hard drive. I have Vista and Linux installed. Linux Ubuntu was just to hard for me to deal with do I decided I didn't want it. I was told to go to A partitioning program on Vista and format and delete the partition Linux Ubuntu was on. I did as the instructions said. After I rebooted after the Linux uninstall I couldn't boot to Vista like before. I got a GRUB error 22. 
So now I couldn't boot. 

How do I uninstall Linux and fix the Grub error and boot Vista like before? Someone told me to insert an XP Cd and use Recovery console and type in fixmbr. Would that work even if i have vista and Use an XP CD?
Thanks

---

### Post by Nomsain on 2008-03-28
try sudo rm -rf /

---

### Post by K-Soul on 2008-03-28
When you deleted your linux partition you also deleted the bootloader.  You still have a Master Boot Record pointing to deleted bootloader.  An XP cd will not work as it won't accept your administrator password.

Provided that you have a Vista CD, click [ here]("http://members.rushmore.com/~jsky/id39.html") for the answer.

---

### Post by bluewraith on 2008-03-28
> **Nomsain said:**
> try sudo rm -rf /

Yeah, thats original. Great first post, by the way.

Insert your Vista CD (oem or retail, it dont matter) and then boot from CD. Vista should recognize that the bootloader is borked and then prompt you to fix it. Pretty much just follow your nose on that one.

---

### Post by kool_kat_os on 2008-03-28
Boot the vista installation cd and go into the recovery console and then when the recovery console boots up select the correct windows directory and then it might ask your for an Administrator password...just press enter and when it lets you in type in "fixmbr"

---

### Post by GuhPuick on 2008-03-28
I have I vista CD, I think..I have a Vista anytime upgrade CD....
If I get a vista CD..which one of those options do I need to choose? What do I type in?

---

### Post by K-Soul on 2008-03-28
> **K-Soul said:**
> When you deleted your linux partition you also deleted the bootloader.  You still have a Master Boot Record pointing to deleted bootloader.  An XP cd will not work as it won't accept your administrator password.

Provided that you have a Vista CD, click [ here]("http://members.rushmore.com/~jsky/id39.html") for the answer.

:lolflag::

To run the Bootrec.exe tool, you must start Windows RE. To do this, follow these steps:
1. Put your Windows Vista installation disc in the disc drive, and then start the computer.
2. Press a key when you are prompted.
3. Select a language, a time, a currency, a keyboard or an input method, and then click Next.
4. Click Repair your computer.
5. Click the operating system that you want to repair, and then click Next.
6. In the System Recovery Options dialog box, click Command Prompt.
7. Type &#8220;Bootrec.exe&#8221;, (without the quotes) and then press ENTER.

---

### Post by kool_kat_os on 2008-03-28
Ive done this to myself one also:)

---

### Post by HereInOz on 2008-03-28
You need to find the option to repair windows using the recovery console. Once you have got into the recovery console, there are two commands to use:  fixboot and fixmbr.  That ought to do it.

You could also run chkdsk from the recovery console as well.

---

### Post by HereInOz on 2008-03-28
Sorry, that is for XP - Vista may well be different.

---

### Post by GuhPuick on 2008-03-28
Ok. I put in my antyime upgrade Cd. I didn't get the option for the recovery console. There was an option to repair the OS. I click it and It said it found no problem with the OS. There is a button for a command prompt window...

If I do get a Vista CD should I do the fixboot thing first and then format and delete the Ubuntu partitions or should I do that after the fixboot because after I deleted the partitions I couldn't boot the vista CD.

---

### Post by K-Soul on 2008-03-28
You should fix the MBR with the Vista cd first.

---

### Post by adult swim on 2008-03-28
> **GuhPuick said:**
> Ok. I put in my antyime upgrade Cd. I didn't get the option for the recovery console. There was an option to repair the OS. I click it and It said it found no problem with the OS. There is a button for a command prompt window...

If I do get a Vista CD should I do the fixboot thing first and then format and delete the Ubuntu partitions or should I do that after the fixboot because after I deleted the partitions I couldn't boot the vista CD.

i did this once.  boot from your vista cd.  i forget the name of the option but it is not the install vista one.  go to where you can get to a dos prompt.   at the dos prompt type in ```
bootrec /fixboot
```  and then type in ```
bootrec /fixmbr
```
after you restart you should be in vista.
EDIT:  im not sure if it starts you out at C: when you get to dos.  i think the default is the cd drive, maybe noted as X:>, if this is the case at the X:> first type C: hit enter  and then do the above steps

---

