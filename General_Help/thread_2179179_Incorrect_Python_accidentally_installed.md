---
title: "Incorrect Python accidentally installed"
date: 2013-10-07
forum: General Help
---

### Post by kaurie on 2013-10-07
I was trying to install a scientific package and Python-2.5.4 was accidentally installed. 

Now every time I run python Python 2.5.4 is run

I still have python2.7 installed in /usr/bin and in this bin ls -ls python*
gives the output
python -> python2.7

I have no idea what I have done and would like to uninstall phython2.5.4

Does anyone know what I should do?

---

### Post by oldfred on 2013-10-07
That link looks correct. Python should be linked to python 2.7. 
Normally you can have many versions of python installed but only one is linked to python and one to python3.
Then you run the other versions by being explicit in version number.
Did somehow 2.7 get overwritten. That should not normally happen.

My python links.
```
fred@fred-Precise:~$ cd /usr/bin
fred@fred-Precise:/usr/bin$ ls -ls python*
   0 lrwxrwxrwx 1 root root       9 Jun 18 12:26 python -> python2.7
   0 lrwxrwxrwx 1 root root       9 Jun 18 12:26 python2 -> python2.7
2920 -rwxr-xr-x 1 root root 2989496 Sep 26 15:29 python2.7
   4 -rwxr-xr-x 1 root root    1652 Sep 26 15:28 python2.7-config
   0 lrwxrwxrwx 1 root root      16 Jun 18 12:26 python2-config -> python2.7-config
   0 lrwxrwxrwx 1 root root       9 Apr 10 16:12 python3 -> python3.2

```

---

### Post by kaurie on 2013-10-07
Thanks for the reply
1 I think (am almost sure) that 2.7 is not overwritten
2 I would like to use the terminal so that when I type python I use pyhton 2.7. Is there an easy way to reset the links
3 I do not know how to get python links (like you did) (Sorry I am ignorant of some Linux)

---

### Post by oldfred on 2013-10-07
I posted the commands with my output above.
cd /usr/bin
ls -ls python*

Then just copy & paste from terminal. Use code tags easily from advanced editor # icon.

---

### Post by kaurie on 2013-10-07
Ops - how embassaring I did not read your code properly 

> lpa@CLINO:/etc$ cd /usr/bin
lpa@CLINO:/usr/bin$ ls -ls python*
   0 lrwxrwxrwx 1 root root       9 Jun 19 03:26 python -> python2.7
   0 lrwxrwxrwx 1 root root       9 Jun 19 03:26 python2 -> python2.7
2920 -rwxr-xr-x 1 root root 2989496 Sep 27 06:29 python2.7
   4 -rwxr-xr-x 1 root root    1652 Sep 27 06:28 python2.7-config
6172 -rwxr-xr-x 1 root root 6318332 Sep 27 05:43 python2.7-dbg
   4 -rwxr-xr-x 1 root root    1656 Sep 27 06:29 python2.7-dbg-config
   0 lrwxrwxrwx 1 root root      16 Jun 19 03:26 python2-config -> python2.7-config
   0 lrwxrwxrwx 1 root root      13 Jun 19 03:26 python2-dbg -> python2.7-dbg
   0 lrwxrwxrwx 1 root root      20 Jun 19 03:26 python2-dbg-config -> python2.7-dbg-config
   0 lrwxrwxrwx 1 root root      16 Jun 19 03:26 python-config -> python2.7-config
   0 lrwxrwxrwx 1 root root      13 Jun 19 03:26 python-dbg -> python2.7-dbg
   0 lrwxrwxrwx 1 root root      20 Jun 19 03:26 python-dbg-config -> python2.7-dbg-config

I am sorry to be dense but can you tell me how to change the link (is it called the symbolic link) to run the 2.7 version. When I run in the terminal (at present) I get

> lpa@CLINO:/usr/bin$ python
Python 2.5.4 (r254:67916, Sep 27 2012, 13:12:30) 
[GCC 4.6.3] on linux3


---

### Post by oldfred on 2013-10-07
All the links are saying they go to 2.7??
So I do not know how running python gives you the 2.5 version.

I prefer synaptic as it shows more. But many parts of Ubuntu need the correct python version.
Can you run this:
sudo apt-get install synaptic
Then from gui, search for synaptic and run that.
In synaptic search, put in python. What version(s) does it show. And for 2.7 click on reinstall and run that.
If not we can run from command line if necessary.

I found this in my notes. May be better?
 [http://ubuntuforums.org/showthread.php?t=2110364](http://ubuntuforums.org/showthread.php?t=2110364)
python --version
sudo update-alternatives --config python

---

### Post by kaurie on 2013-10-08
Thanks again for the help

I will wait till the weekend to try this and let you know what the outcome was.

---

### Post by Vaphell on 2013-10-08
how exactly did you accidentally install python 2.5.4?

---

### Post by kaurie on 2013-10-12
Vaphell - I was installing a scientific package from the web and did not check it carefully enough. This packae automatically intalled python 2.5.4 - where I was not sure

---

### Post by kaurie on 2013-10-12
OK I am now geting somewhere.

I finally looked at PATH
> lpa@CLINO:/usr/bin$ echo $PATH
/usr/lib/lightdm/lightdm:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games


So I found python 2.5.4 installed in /usr/local/bin
> lpa@CLINO:/usr/local/bin$ ls -ls python*
5120 -rwxr-xr-x 2 root root 5242800 Sep 27  2012 python
5120 -rwxr-xr-x 2 root root 5242800 Sep 27  2012 python2.5
   4 -rwxr-xr-x 1 root root    1424 Sep 27  2012 python2.5-config
   0 lrwxrwxrwx 1 root root      16 Sep 27  2012 python-config -> python2.5-config


lpa@CLINO:/usr/local/bin$ ls
bsp_virtual  ncgen     pyro-genguid  pyro-rns    python2.5         task_manager
f2py         pydoc     pyro-ns       pyro-wxnsc  python2.5-config  tviewer
idle         pyro-es   pyro-nsc      pyro-xnsc   python-config
ncdump       pyro-esd  pyro-nsd      python      smtpd.py


AND when I am in /usr/bin and run python2.7

> lpa@CLINO:/usr/bin$ python2.7
Python 2.7.3 (default, Sep 26 2013, 20:03:06) 
[GCC 4.6.3] on linux2
Type "help", "copyright", "credits" or "license" for more information.


SO

I think that I need to disable the links in  /usr/local/bin and I will be OK

ANY Comments

---

### Post by kaurie on 2013-10-13
OK it is solved

I finally tracked down the setup in the install files and found that python 2.5 was installed on  /usr/local/bin

[LIST=1]
[*]I renamed the python file there to something else
[*] Rebooted 
[*]opened a terminal in the home directory
[*]Typed python which gave the correct version number
[/LIST]



Again Thanks for the help

---

### Post by Laurence02 on 2013-10-13
Seems good, my friend. No pro myself, but keep going!

---

