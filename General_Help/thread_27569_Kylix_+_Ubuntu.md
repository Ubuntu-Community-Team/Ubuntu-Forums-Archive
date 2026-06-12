---
title: "Kylix + Ubuntu"
date: 2005-04-16
forum: General Help
---

### Post by Kryton on 2005-04-16
Hi,
  I've been trying to install Kylix 3 onto my fresh Ubuntu install. Has anyone managed to get it working? At present it has installed fine and I have made sym. links to the various things that are missing (due to versioning in names) and apparently that should work fine. However, when trying to "startdelphi" all I end up with is a grey screen with the tool windows all minimised. If I try and restore/position these then they show but no text appears and I have no control/menu pallette at the top.

Does anyone have any suggestions?

-  Kryton

---

### Post by Kryton on 2005-04-18
Bump  :wink:

---

### Post by tread on 2005-04-18
Try starting it from the commandline (if possible, with a verbose option) and then observe the messages that get printed out (on stderr). That might give you some clue .. I managed to find a problem with an application that used libpng, but got the wrong version.

---

### Post by eric222 on 2005-04-20
I too have this problem with Kylix Pro 3.  It installs fine, but after launching it the menues and toolbar are all over the place or missing and most of the screen is just grey.  I will probably spend a little time trying to figure it out again, but if anyone has some suggestions.....

---

### Post by dekae on 2005-05-11
I have the same problem too. Did anyone solve it?
thank you

Alvaro

---

### Post by orangepeel on 2005-05-17
From what I understand of it (and I'm real noob at this) Kylix can only use X11. If you use XFree then you get the issues u guys describe.

I had it working fine on warty but can't get it going at all with hoary.

If you manage to work out how to use X11 with hoary then it should work. I've never had any joy there so can't really help any further.

---

### Post by orangepeel on 2005-05-20
[QUOTE=orangepeel]From what I understand of it (and I'm real noob at this) Kylix can only use X11. If you use XFree then you get the issues u guys describe.

I had it working fine on warty but can't get it going at all with hoary.

If you manage to work out how to use X11 with hoary then it should work. I've never had any joy there so can't really help any further.[/QUOTE]

ok apparently I'm getting my x's mixed up.

Kylix works with XFree86. Hoary comes with X.org (??) If you can get XFree86 working on Hoary (no idea how. Help?) then kylix should work.

---

### Post by Omnix on 2005-05-20
Ok, figured it out on Hoary - should be able to port to other versions/Debian-based distros if required :) 

First off, libX11.so that the install script searches for doesn't exist, link to the current library version:
$ sudo ln -s /usr/X11R6/lib/libX11.so.6 /usr/X11R6/lib/libX11.so

Install GTK 1.2 and Xaw6 libraries (7 and 8 are installed by default)
$ sudo apt-get install libgtk1.2 libxaw6

Install with:

$ ./setup.sh

Once installed, you need to fix the grey windows/no text/icons problem.  Open up "startdelphi" in your favourite text editor or:

$ nano `which startdelphi`

At the top, it has this by default:
```
KYDEF_LOCALE="en_US"
``` 

This loads Kylix in UTF-8 mode by default, which it doesn't seem to like.  Simply change to this for the US:
```
KYDEF_LOCALE="en_US.ISO8859-1"
``` 

Great Britain:
```
KYDEF_LOCALE="en_GB.ISO8859-1"
``` 

etc, replacing your country's ISO code with the appropriate value.

For the last bit, scroll to the last line of the file where it has something like:
```
/home/user/kylix3/bin/delphi $*
```

Change it to:
```
LANG=$KYDEF_LOCALE /home/user/kylix3/bin/delphi $*
```

Then just start Kylix as normal, using the menu or startdelphi command.

Hope this helps :)

---

### Post by orangepeel on 2005-05-21
cheers om, that worked nice.

---

### Post by lvincent on 2005-06-17
thank you so much for the fix. your such an angel :). but there's still an evil inside my kylix because it will hang when i run a simple app.  any idea how to solve this one? 

or have you true doing a fix that goes something like this LD_ASSUME_KERNEL?


THANKS,

lvincent

---

### Post by josir on 2005-09-07
Hi folks,

I installed Kylix 3 OE with the tips you posted. Thanks a lot!
I spent 2 weeks trying to install Kylix on Mandrake 10... 
With Ubuntu it take me just 6h!!!

But nothing is perfect..
When I try to run with debugging, Kylix freezes. Do you have any suggestion?
When I disable Integrated Debugging it works fine.

I added the "export LD_ASSUME_KERNEL=2.4.1" to startdelphi script but it doesn't work either.

Any tip will be welcome!
Josir.

---

### Post by 89c51 on 2005-09-12
i'm also having problems with kylix 3 open

the instalation is fine but

1)no icons are generated on the menu
2)when i try to start kylix with startbcd (in order to have c++) it just doesnt start

thanks

---

### Post by josir on 2005-11-07
Hi folks, 

I made a tutorial to install Kylix on Ubuntu based on your posts.
It's in portuguese but you can get the main ideas and commands.

[www.jsk.com.br/kylix-ubuntu.html](www.jsk.com.br/kylix-ubuntu.html)

Thank you all,
Josir Gomes
Rio de Janeiro - Brasil

---

### Post by lucasvasconcelos on 2005-11-07
hi folks, i install Kylix 3 on Ubuntu 5.10 and disable the integrated debuging. 

now i'm trying install the Indy 10 and zeosdbo 6.5 alpha but kylix frozzen when i run "install" command.

someone can help-me ? :???: 

 thanks

PS: josir seu artigo foi bastante esclarecedor, mas n&#227;o consegui resolver meus problemas :(

---

### Post by borland-c on 2006-12-30
> **Omnix said:**
> $ sudo apt-get install libgtk1.2 libxaw6```
dpkg: failed to open package info file `/var/lib/dpkg/available' for reading: No such file or directory
E: Sub-process /usr/bin/dpkg returned an error code (2)
```was mache ich falsch?

---

### Post by diepruis on 2006-12-30
> **borland-c said:**
> ```
dpkg: failed to open package info file `/var/lib/dpkg/available' for reading: No such file or directory
E: Sub-process /usr/bin/dpkg returned an error code (2)
```was mache ich falsch?

Bitte frage auf Anglisch. Kein hier versteht Deutsch.

---

### Post by borland-c on 2006-12-30
> **diepruis said:**
> Bitte frage auf Anglisch. Kein hier versteht Deutsch.I'm sorry
I cann't install libgtk1.2, please recommend repositories, from which I can install this one, thank you

---

### Post by diepruis on 2006-12-31
> **borland-c said:**
> I cann't install libgtk1.2, please recommend repositories, from which I can install this one, thank you

Did you enable the Universe repository?

---

### Post by borland-c on 2007-01-03
> **diepruis said:**
> Did you enable the Universe repository?yes, that was else problem and I have already fixed it, thanks you for attention and sorry for trouble
finally I  Install Kylix  :rolleyes:

---

### Post by calvin&amp;hobbs on 2007-03-13
Hi there all

I'm a REAL no0b in Linux, and I was given the task to install Kylix on my Machine with Ubuntu 6.10. When I try to run the setup file, this message is given

> root@Ubuntu:/home/frank# cd /media/cdrom
root@Ubuntu:/media/cdrom# sudo sh setup.sh
setup.sh: 93: Syntax error: "(" unexpected
root@Ubuntu:/media/cdrom# 

in the terminal. Can ANYONE help me!!!

Thanks

---

### Post by diepruis on 2007-03-13
This might be because Ubuntu 6.10 uses the Dash shell, while that script was probably written for Bash. You can try to fix it yourself with information from the 'net, or ask someone here, or even ask over at Borland. You might even try running the script in Bash. To do that, you can open a terminal and issue the "bash" command, then try to execute the installer.

Good luck.

---

### Post by calvin&amp;hobbs on 2007-03-19
Hi there, thanks I got it to install on ubuntu. Now for the next problem. I can not find the startdelphi executable. The link is there but no start delphi. What did I do wrong!?

---

### Post by tlacuache on 2007-03-19
As a developer who used to use Kylix a lot (back when it was being actively developed and supported), I spent a lot of hours battling with it and finally got it to work on Dapper. When I upgraded to Edgy, it broke and I couldn't get it working again (it would actually crash with an access violation when I tried to run it).

What I finally ended up doing was dropping Kylix altogether and started using Lazarus and FreePascal (see [http://www.lazarus.freepascal.org](http://www.lazarus.freepascal.org) and [http://www.freepascal.org)](http://www.freepascal.org)). Lazarus/FreePascal has allowed me to do everything I ever needed to do in Kylix, with MUCH better Linux support. Plus, it's being actively developed and maintained, so there's a lot less likelihood that you'll run into some show-stopper like you might in Kylix (which Borland won't fix since they don't maintain or support it).

Just a suggestion.

---

