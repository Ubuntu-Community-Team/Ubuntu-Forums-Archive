---
title: "Brother Printer Install Tool Not Loading Via Terminal command"
date: 2018-01-18
forum: General Help
---

### Post by Nylo on 2018-01-18
Brother's printer install tool is installed on my system, but when I try and run it 
it says, "cups not installed."  The install tool is suppose to install cups and all the drivers.

What I have done.
- Uninstalled everything relating to Brothers... Drivers & folders. = CUPS is not installed
- Installed ALL of the cups & drivers from Brother's support page. = CUPS is not installed

No matter what I do its always, "cups not installed."  Whats strange is Im running 
a tower with Lubu 16.04 LTS and I was able to make the install tool work.  I just 
cannot remember what I did.  Could not find any answers on Google.

```
**@**:~$ cd Downloads
**@**:~/Downloads$ sudo bash linux-brprinter-installer-2.2.0-1 HL-L2320D
[sudo] password for **: 
CUPS is not installed.
**@**:~/Downloads$
```

---

### Post by DuckHook on 2018-01-18
```
apt policy cups
```…please post output. If not installed, do:```
sudo apt update && sudo apt install cups
```

---

### Post by Nylo on 2018-01-18
Was not installed.

Your request:

```
**@**:~$ apt policy cups
cups:
  Installed: 2.1.3-4ubuntu0.3
  Candidate: 2.1.3-4ubuntu0.3
  Version table:
 *** 2.1.3-4ubuntu0.3 500
        500 ]http://mirror.math.ucdavis.edu/ubuntu xenial-updates/main amd64 Packages
        100 /var/lib/dpkg/status
     2.1.3-4 500
        500 [http://mirror.math.ucdavis.edu/ubuntu](http://mirror.math.ucdavis.edu/ubuntu) xenial/main amd64 Packages
```

---

### Post by DuckHook on 2018-01-18
Please post your output between [noparse]```
 and 
```[/noparse] tags for clarity. Or highlight the output and use the [img]http://ubuntuforums.org/images/editor/code.gif[/img] button in the *Adv Reply* toolbar.

Hmmm&#8230;

Will have to do some research and ponder this one a little.

---

### Post by Nylo on 2018-01-18
It worked... Sorta.  Now Im getting this.  I only want a USB connect.

Will you specify the Device URI? [Y/n] ->n

Test Print? [y/N] ->y

wait 5s.
lpr -P HLL2320D /usr/share/cups/data/testprint
linux-brprinter-installer-2.2.0-1: line 2951: lpr: command not found
ls: cannot access '/etc/udev/rules.d/*.rules': No such file or directory
**@**:~/Downloads$

---

### Post by Nylo on 2018-01-18
It will not do a test print, but does PRINT!!!!!!

Thank you so much for your knowledge and fast reply.

---

### Post by DuckHook on 2018-01-18
> **Nylo said:**
> It will not do a test print, but does PRINT!!!!!!

Thank you so much for your knowledge and fast reply.
:lolflag:

I've done ***nothing!*** This is all to your own credit. It's very heartwarming when users progress without a shred of input from we old-timers. If you still want to chase down the wonkiness of your situation, then keep this thread open and see what other responses you get. However, in my experience, once something is working, it is bad luck to look a gift horse in the mouth.

Good Luck and Happy Ubuntu-ing!

---

### Post by VMC on 2018-01-19
Sometimes it just takes an "ear" to send us on our way.

Also, have you installed the Brothers drivers? Found here:
[http://support.brother.com/g/b/downloadlist.aspx?c=as_ot&lang=en&prod=hll2320d_us_as&os=128](http://support.brother.com/g/b/downloadlist.aspx?c=as_ot&lang=en&prod=hll2320d_us_as&os=128)

Now that Cups is installed, visit:
[http://localhost:631/admin](http://localhost:631/admin)
and you can invistigate further.

BTW, I have that exact same Brother printer. I was using a dot matrix printer, but every time I would want to print something, the ink was dried out.
Also I was able to print a text page, maybe after installing the drivers. Not sure right now. I haven't used it in a while. I'll check in a while.

---

### Post by Nylo on 2018-01-19
I though the Brother install tool does this.

> **VMC said:**
> 

Also, have you installed the Brothers drivers? Found here:
[http://support.brother.com/g/b/downloadlist.aspx?c=as_ot&lang=en&prod=hll2320d_us_as&os=128](http://support.brother.com/g/b/downloadlist.aspx?c=as_ot&lang=en&prod=hll2320d_us_as&os=128)



---

