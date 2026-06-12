---
title: "Force Quit PDF"
date: 2015-03-04
forum: General Help
---

### Post by SuperFreak on 2015-03-04
For some time (a month or so) everytime I try to close a PDF file the file won't close until eventually I am given the option to Force Quit the application which does close it. Is there a bug or problem that has been introduced from recent updates of 14.04.2?

---

### Post by ajgreeny on 2015-03-04
Are you using Ubuntu with evince or some other application to view the PDF?

Does this happen with every PDF file or just one or two?  Where did the PDFs come from; how were they produced?

You can find the version of PDF with command **file filename.pdf** in terminal; perhaps different PDF versions cause this problem, though all seem to open, display and close fine on my system, though very occasionally I have printing problems from evince and have to use either qpdfview or okular.

---

### Post by SuperFreak on 2015-03-04
Yes I use Evince and it seems to happen on all PDF files virtually all of which were downloaded files.
The command says that I have PDF document, version 1.4


EDIT: I switched default viewer to qpdfviewer and now documents close properly

---

### Post by tgalati4 on 2015-03-04
*evince* does not appear to have a --debug switch.  Open a terminal and run *evince* with the pdf filename that you want to open.  See if any error messages show up in the terminal.  Then try to close the program and see if any messages come up.  If the program won't close, then hit Control-C while in the terminal window to kill it.  Post anything useful.  Try using the --g-fatal-warnings switch.

---

### Post by SuperFreak on 2015-03-04
No error messages when opening file but got these messgaes when closing using CTL C (PDF would not close normally)


```
david@MainSqueeze:/media/Documents/Documents/David/Tech/Manuals/TV/Samsung LNT 3242 H$ evince Samsung\ LNT\ 3242H.pdf

** (evince:12759): WARNING **: Timeout was reached

** (evince:12759): WARNING **: Timeout was reached

** (evince:12759): WARNING **: Timeout was reached

** (evince:12759): WARNING **: Timeout was reached

** (evince:12759): WARNING **: Timeout was reached

** (evince:12759): WARNING **: Timeout was reached

** (evince:12759): WARNING **: Timeout was reached

** (evince:12759): WARNING **: Timeout was reached

** (evince:12759): WARNING **: Timeout was reached

** (evince:12759): WARNING **: Timeout was reached
^C
david@MainSqueeze:/media/Documents/Documents/David/Tech/Manuals/TV/Samsung LNT 3242 H$ 

```

---

### Post by tgalati4 on 2015-03-05
Try again with:

```
evince --g-fatal-warnings Samsung.pdf
```

The timeout warning could be coming from the watchdog timer, which triggers whenever a process sends a message and that message is not responded to in a timely fashion.  This implies a stuck process (which appears to be the case).  So only a force-quit will kill it.  Now to figure out why evince is behaving this way.

Next time you kill evince (force-quit or Control-C in a terminal), open another terminal and examine the output of:

```
dmesg | tail -50
```  

Only post error messages related to this problem, since dmesg can put out a lot of stuff.

---

### Post by SuperFreak on 2015-03-05
evince -g-fatal-warnings switch

```
david@MainSqueeze:/media/Documents/Documents/David/Tech/Manuals/TV/Samsung LNT 3242 H$ evince -g-fatal-warnings switch Samsung\ LNT\ 3242H.pdf
Cannot parse arguments: Unknown option -g-fatal-warnings

```

Tried dmesg | tail -50 but I am not able to find any  mention of EVINCE in the output and not sure what to look for

---

### Post by ajgreeny on 2015-03-05
There should be two --  at the start of the **--g-fatal-warnings** switch, which even tgalati4 did not get right in his last post.

That's typos for you; they always creep in just when you really don't want them!

---

### Post by SuperFreak on 2015-03-05
Thanks ajgreeny

```

david@MainSqueeze:/media/Documents/Documents/David/Tech/Manuals/TV/Samsung LNT 3242 H$ evince --g-fatal-warnings switch Samsung\ LNT\ 3242H.pdf
** (evince:7997): WARNING **: Error when getting information for file '/media/Documents/Documents/David/Tech/Manuals/TV/Samsung LNT 3242 H/switch': No such file or directory
Trace/breakpoint trap (core dumped)
david@MainSqueeze:/media/Documents/Documents/David/Tech/Manuals/TV/Samsung LNT 3242 H$ 
** (evince:8005): WARNING **: Timeout was reached

** (evince:8005): WARNING **: Timeout was reached

** (evince:8005): WARNING **: Timeout was reached

** (evince:8005): WARNING **: Timeout was reached

** (evince:8005): WARNING **: Timeout was reached

** (evince:8005): WARNING **: Timeout was reached

** (evince:8005): WARNING **: Timeout was reached

** (evince:8005): WARNING **: Timeout was reached

** (evince:8005): WARNING **: Timeout was reached

** (evince:8005): WARNING **: Timeout was reached

** (evince:8005): WARNING **: Timeout was reached

** (evince:8005): WARNING **: Timeout was reached

** (evince:8005): WARNING **: Timeout was reached

** (evince:8005): WARNING **: Timeout was reached

** (evince:8005): WARNING **: Timeout was reached

** (evince:8005): WARNING **: Timeout was reached

** (evince:8005): WARNING **: Timeout was reached

** (evince:8005): WARNING **: Timeout was reached

** (evince:8005): WARNING **: Timeout was reached

** (evince:8005): WARNING **: Timeout was reached


```


I am not quite sure what I am looking for with dmesg | tail -50 but I found this:


```
2486 PROTO=TCP SPT=443 DPT=40940 WINDOW=0 RES=0x00 RST URGP=0 
[10892.112827] traps: evince[7997] trap int3 ip:7f151e4a2c13 sp:7fff64232190 error:0
[10939.582893] [UFW BLOCK] IN=eth0 OUT= MAC=01:00:5e:00:00:01:f8:1a:67:f0:7e:86:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[11015.213778] [UFW BLOCK] IN=eth0 OUT= MAC=bc:5f:f4:3b:99:82:f8:1a:67:f0:7e:86:08:00 SRC=74.125.202.132 DST=192.168.1.103 LEN=40 TOS=0x00 PREC=0x00 TTL=48 ID=38166 PROTO=TCP SPT=443 DPT=53000 WINDOW=0 RES=0x00 RST URGP=0 

```

---

### Post by tgalati4 on 2015-03-05
Sorry about the typo.  There is no "switch" in the command:

```
evince --g-fatal-warnings Samsung.pdf
```

It looks like an error in the metadata of the file.

What does this command say?

```
file Samsung.pdf
```

Are you having problems with just *evince* or with all PDF's that you open with *evince*?

---

### Post by SuperFreak on 2015-03-05
Removed switch

```
david@MainSqueeze:~$ cd /media/Documents/Documents/David/Tech/Manuals/TV/Samsung\ LNT\ 3242\ H
david@MainSqueeze:/media/Documents/Documents/David/Tech/Manuals/TV/Samsung LNT 3242 H$ evince --g-fatal-warnings Samsung\ LNT\ 3242H.pdf

** (evince:4015): WARNING **: Timeout was reached
Trace/breakpoint trap (core dumped)
david@MainSqueeze:/media/Documents/Documents/David/Tech/Manuals/TV/Samsung LNT 3242 H$ 


```

PDF crashed on that command. When I enter dmesg | tail -50
I get this in the output

```
[ 4765.612262] [UFW BLOCK] IN=eth0 OUT= MAC=bc:5f:f4:3b:99:82:f8:1a:67:f0:7e:86:08:00 SRC=173.194.127.216 DST=192.168.1.103 LEN=40 TOS=0x00 PREC=0x00 TTL=54 ID=31034 PROTO=TCP SPT=443 DPT=60135 WINDOW=0 RES=0x00 RST URGP=0 
[COLOR="#FF8C00"][FONT=Arial Black][ 4807.344867] traps: evince[4015] trap int3 ip:7fe52b0d9c13 sp:7fff89c38bd0 error:0[/FONT][/COLOR]
[ 4829.038621] [UFW BLOCK] IN=eth0 OUT= MAC=bc:5f:f4:3b:99:82:f8:1a:67:f0:7e:86:08:00 SRC=173.194.43.96 DST=192.168.1.103 LEN=40 TOS=0x00 PREC=0x00 TTL=58 ID=52
```

when I enter the file Samsung\ LNT\ 3242H.pdf I get

```
david@MainSqueeze:/media/Documents/Documents/David/Tech/Manuals/TV/Samsung LNT 3242 H$ file Samsung\ LNT\ 3242H.pdfSamsung LNT 3242H.pdf: PDF document, version 1.3

```

I don't really use Evince for anything but reading pdfs, but it seems to be problematic with every pdf file I have opened. As noted in the second or third post (in an edit I admit so I hope you noticed) I tried another pdf reader and it works so if this is not a critical problem I am alright with qpdfviewer

---

### Post by tgalati4 on 2015-03-05
Let's try to *remove* evince and reinstall it.

```
sudo apt-get purge evince
sudo apt-get clean
sudo apt-get check
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install evince
```

---

### Post by SuperFreak on 2015-03-05
Worked

Much Thanks:p

I spoke too soon. It worked and I set evince to default reader and am again having same problems

---

### Post by mc4man on 2015-03-05
If you're happy with the other reader then no sense pursuing though have to ask - are you using a default ubuntu 14.04.2 or something else
( see Cinnamon DE mentioned

---

### Post by SuperFreak on 2015-03-05
repeat post. delete

---

### Post by SuperFreak on 2015-03-05
Yes I am using Cinnamon and perhaps that is the problem. Until Ubuntu 14.04.1 updated to the next point release 14.04.2 evince worked without issue. However I will just use the other pdf reader as default. Thanks for your input.

---

### Post by tgalati4 on 2015-03-06
I would file a bug against Cinnamon because this is repeatable behavior.  In the meantime, purge evince and reinstall it and don't set it as default.  Right-click and "Open With" on a PDF file and see if *evince* works correctly.  It's possible that Cinnamon uses a fork of *evince*.  I run MATE and *atril* is the fork of *evince* that works under MATE.

---

### Post by SuperFreak on 2015-03-06
>  I would file a bug against Cinnamon because this is repeatable behavior. In the meantime, purge evince and reinstall it and don't set it as default. Right-click and "Open With" on a PDF file and see if evince works correctly. It's possible that Cinnamon uses a fork of evince. I run MATE and atril is the fork of evince that works under MATE. 


Still doesn't seem to close pdfs correctly.I will file a bug

---

