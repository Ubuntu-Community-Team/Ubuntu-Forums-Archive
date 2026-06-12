---
title: "Sudo apt-get remove error: Can't locate package I just installed"
date: 2013-02-01
forum: General Help
---

### Post by KatyG on 2013-02-01
Hi,

I installed some programs I didn't need and now I'd like to remove them. I installed them using this blog post[ http://xgjonathan.blogspot.com/2011/04/how-to-install-libpcap-on-ubuntu.html]("http://xgjonathan.blogspot.com/2011/04/how-to-install-libpcap-on-ubuntu.html"). 

In the terminal I have tried to use sudo apt-get purge program name, sudo aptitude remove program name, sudo apt-get remove program name.

It says: 
E:  unable to locate package bison 2.7
E: Couldn't find any packages by regex 'bison 2.7'.

If I look at the home folder, there are files by the names I am trying. I just installed them using sudo.

Background: I installed Wireshark for class using the Ubuntu Software center. My computer says there are no network interfaces to capture from. I know this is untrue.

I thought maybe I needed libpcap, as when I searched for it there were no results.

So I used these steps to install the listed programs.


[LIST=1]
[*]Download libpcap-1.3.0.tar.gz from [http://www.tcpdump.org/](http://www.tcpdump.org/) and decompress it;
[*]Download flex-2.5.37.tar.gz from [http://flex.sourceforge.net/](http://flex.sourceforge.net/) and decompress it;
[*]Download bison-2.7.tar.gz from [ftp://ftp.gnu.org/gnu/bison/](ftp://ftp.gnu.org/gnu/bison/) and decompress it;
[*]Download m4-1.4.16.tar.gz from [ftp://ftp.gnu.org/gnu/m4/](ftp://ftp.gnu.org/gnu/m4/) and decompress it;
[*]Then, enter into directories m4-1.4.16, bison-2.7, flex-2.5.37 and libpcap-1.3.0 [COLOR=red]in order[/COLOR], and execute the following commands:
[LIST=1]
[*]$ [COLOR=red]sudo[/COLOR] ./configure
[*]$ [COLOR=red]sudo[/COLOR] make
[*]$ [COLOR=red]sudo[/COLOR] make install.
[/LIST]
 
[/LIST]


Any help?

---

### Post by oldos2er on 2013-02-01
If you compile and install programs from source, apt-get knows nothing about them. You'll need to go back into the source folders and run **sudo make uninstall** for each one. If you want to avoid having to this in the future, try checkinstall: [https://help.ubuntu.com/community/CheckInstall](https://help.ubuntu.com/community/CheckInstall)

Also if you're downloading and compiling source in your home folder, you shouldn't use sudo with either ./configure or make.

---

### Post by KatyG on 2013-02-02
Thank you.

---

