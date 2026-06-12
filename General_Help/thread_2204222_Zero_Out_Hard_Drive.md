---
title: "Zero Out Hard Drive"
date: 2014-02-07
forum: General Help
---

### Post by ron177 on 2014-02-07
I have a 1 TB had drive on my laptop partitioned  into a dual-boot setup for Windows 7 and Ubuntu. I have followed the  instructions given here to zero out the hard drive from within Windows;  or that's what I felt I was doing:
 [http://pcsupport.about.com/od/toolsofthetrade/ht/write-zeros-format-command.htm](http://pcsupport.about.com/od/toolsofthetrade/ht/write-zeros-format-command.htm)
 This seems to have wiped out info on the Windows partition but not on  the Linux one. So now I rebooted my computer and logged into my Ubuntu.  Opened the terminal and typed the following to zero out info on my  other partition:
 sudo dd if=/dev/zero of=/dev/sda
 I don't see anything happening on the terminal, but I feel as though  the computer is working. Am I on the right path? Or have I missed  something?
 All I want to do is to zero out the entire hard drive (all partitions  included) and reinstall Windows before I sell the computer. Can someone  help please?
 Thanks,
 R

---

### Post by andyfied on 2014-02-07
The command looks right to me. How big is the HDD and how long has it been going? It can take a very long time.

---

### Post by sudodus on 2014-02-07
***dd*** is a slow and ineffient tool to wipe a whole big hard disk drive, but it works. See this thread at the Ubuntu Forums [best way to wipe a drive]("http://ubuntuforums.org/showthread.php?t=2124829") for another method using hdparm. See post #12 for details.

-o-

You can make ***dd*** output three lines showing how far it has gone with the following commands from another terminal window

```
ps -A|grep " dd$"
```
and use the pid number (at the beginning of the line)

Let us say that the output is 

 93211 ?        00:00:00 dd

So send the USR1 signal to the process of dd. *Use the output of **your** ps command* (*not* 93211 from my example)

```
sudo kill -USR1  93211
```

This method is [almost] described in the manual ```
man dd
```

```

       Sending a USR1 signal to a running `dd' process makes it print I/O statistics to standard error
       and then resume copying.

              $ dd if=/dev/zero of=/dev/null& pid=$!
              $ kill -USR1 $pid; sleep 1; kill $pid

```

---

### Post by ron177 on 2014-02-07
I just realized that I should [LEFT][COLOR=#444444][FONT=UbuntuRegular]not be doing it from my boot disk. If I boot from sda which I did and I want to erase sda, the process does not go to the end? Is that what it is? Should I have booted from a LiveCD to make sure the process goes to the end? [/FONT][/COLOR][COLOR=#444444][FONT=UbuntuRegular]
[/FONT][/COLOR][/LEFT]

---

### Post by sudodus on 2014-02-07
> **ron177 said:**
> I just realized that I should [LEFT][COLOR=#444444][FONT=UbuntuRegular]not be doing it from my boot disk. If I boot from sda which I did and I want to erase sda, the process does not go to the end? Is that what it is? Should I have booted from a LiveCD to make sure the process goes to the end? [/FONT][/COLOR][COLOR=#444444][FONT=UbuntuRegular]
[/FONT][/COLOR][/LEFT]


Yes, boot from another drive, your Ubuntu install CD/DVD/USB drive is fine as a live drive. Otherwise you will be 'sawing the branch that you are sitting on'.

But unless you have data, that you think are very secret, you need only wipe the first megabyte for a new partition table to be clean.

---

### Post by ron177 on 2014-02-07
Oh thanks. This is very helpful.

---

