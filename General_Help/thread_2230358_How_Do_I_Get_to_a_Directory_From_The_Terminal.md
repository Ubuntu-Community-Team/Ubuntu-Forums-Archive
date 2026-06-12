---
title: "How Do I Get to a Directory From The Terminal?"
date: 2014-06-18
forum: General Help
---

### Post by wbee on 2014-06-18
Hello,

[http://support.brother.com/g/b/downloadhowto.aspx?c=us&lang=en&prod=mfcj450dw_us&os=128&dlid=dlf006893_000&flang=4&type3=625]("http://support.brother.com/g/b/downloadhowto.aspx?c=us&lang=en&prod=mfcj450dw_us&os=128&dlid=dlf006893_000&flang=4&type3=625")

The link above gives the instructions to install the printer and scanner drivers in a printer that is not in the CUPS data base.

I downloaded the driver install tool,which went into the download directory correctly.

When I attempted step three,the terminal told me it could not find the directory.

Could you explain step two to me? That is,how do I use the terminal to get to the correct directory?

With Ubuntu 12.04,can it be in the download directory or should I move it to the home directory?

When I get to the correct directory,should the rest of the installation be fairly straight forward? Will the terminal allow me to select the installer tool?

------------

Thank you.

---

### Post by grahammechanical on 2014-06-18
We use a command to change directory (cd). So, to change to the Downloads directory type

```
cd Downloads
```

The prompt will change from ~$ to ~/Downloads$. That how we know which directory we are working in. I also use the list command (ls) to show me what is in the directory. So running 

```
ls
```

when we first open the terminal will show

> Desktop    Downloads         Music     Public     Videos
Documents  examples.desktop  Pictures  Templates




to move back out into the directory we came from

```
cd ..
```

Be careful. The terminal is case sensitive. So, if a command does not work check that the command is typed correctly.

Regards.

---

### Post by sammiev on 2014-06-18
> **wbee said:**
> Hello,

[http://support.brother.com/g/b/downloadhowto.aspx?c=us&lang=en&prod=mfcj450dw_us&os=128&dlid=dlf006893_000&flang=4&type3=625]("http://support.brother.com/g/b/downloadhowto.aspx?c=us&lang=en&prod=mfcj450dw_us&os=128&dlid=dlf006893_000&flang=4&type3=625")

The link above gives the instructions to install the printer and scanner drivers in a printer that is not in the CUPS data base.

I downloaded the driver install tool,which went into the download directory correctly.

When I attempted step three,the terminal told me it could not find the directory.

Could you explain step two to me? That is,how do I use the terminal to get to the correct directory?

With Ubuntu 12.04,can it be in the download directory or should I move it to the home directory?

When I get to the correct directory,should the rest of the installation be fairly straight forward? Will the terminal allow me to select the installer tool?

------------

Thank you.

grahammechanical likely said it all. 
Check out my sig for terminal commands.

---

### Post by pdc on 2014-06-19
so wbee: the commands from opening a terminal would be: (they are in red, and you can copy and paste them into a terminal):

[COLOR="#FF0000"]cd Downloads[/COLOR]  (as so well covered by grahammechanical)
[COLOR="#FF0000"]gunzip linux-brprinter-installer-2.0.0-1.gz[/COLOR]
[COLOR="#FF0000"]sudo bash linux-brprinter-installer-2.0.0-1 MFC-J450DW[/COLOR] (you will need your sudo password)

.........that should launch the installer, and others report it works very well

---

### Post by wbee on 2014-06-19
Thanks you all.

---

### Post by pdc on 2014-06-19
all should be good now and enjoy your printer

---

