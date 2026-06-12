---
title: "testdisk used, any other option to try and recover data?"
date: 2017-09-02
forum: General Help
---

### Post by bold33 on 2017-09-02
Hi,

I managed to run testdisk on an image I made in my computer. With this command

```
sudo testdisk damaged-usb.img
```

the INTEL partition and the advanced option the BS was reconstructed ans some files, but not the directories, were recognizable:

```
>-rwxr-xr-x   0   0   3224587 21-Apr-2011 21:22 Radiohead - OK Computer.pdf
 -rwxr-xr-x   0   0   5991678 21-Apr-2011 23:53 Rage Against the Machine - The Battle of Los Angeles.pdf
 -rwxr-xr-x   0   0   7550469 22-Apr-2011 15:32 Metallica - Kill'em All.pdf
 -rwxr-xr-x   0   0  61708657 23-Apr-2011 22:19 Megadeath - Rust In Peace.pdf
 -rwxr-xr-x   0   0  53250131 24-Apr-2011 13:35 Oasis - Definitely Maybe.pdf
 -rwxr-xr-x   0   0  15175395 23-Apr-2011 00:22 Deep Purple - Best of.pdf
```

in some other clusters there are also recognizable files of programs I had installed in the usb unit (and also readable in the image).

In other clusters, I get something like this:

```
 -r-xr-xr-x   0   0 2744836514 20-Nov-1924 22:44 ~Z~Y&#5786;&#5787;.&#5788;
 -r-xr-xr-x   0   0 2598481306 26-May-1921 16:00 &#5796;&#5797; M-&^J
 -r-xr-xr-x   0   0 2208031106 21-Nov-1908 22:43 ~ZM-9&#5818;&#5819;.&#5820;
 -r-xr-xr-x   0   0 2615250331 26-Nov-1920 12:00 &#5828;&#5829; ~F^J
 -r-xr-xr-x   0   0 2744902050 21-Nov-1924 22:44 ~[~Y&#5850;&#5851;.&#5852;
 -r-xr-xr-x   0   0 2615258523 26-Nov-1920 16:00 &#5860;&#5861; M-&^J
 -r-xr-xr-x   0   0 2208096642 22-Nov-1908 22:43 ~[M-9  . 
 -r-xr-xr-x   0   0 2632027548 26-May-1922 12:00 &#5892;&#5893; ~F^J
 -r-xr-xr-x   0   0 2744967586 22-Nov-1924 22:44 ~\~Y  . 
 -r-xr-xr-x   0   0 2632035740 26-May-1922 16:00 &#5924;&#5925; M-&^J
 -r-xr-xr-x   0   0 2208162178 23-Nov-1908 22:43 ~\M-9  . 
 -r-xr-xr-x   0   0 2648804765 26-Nov-1921 12:00 &#5956;&#5957; ~F^J
 -r-xr-xr-x   0   0 2745033122 23-Nov-1924 22:44 ~]~Y  . 
 -r-xr-xr-x   0   0 2648812957 26-Nov-1921 16:00 &#5988;&#5989; M-&^J
```

sometimes with chinese characters:

 ```
-r-xr-xr-x   0   0 3837298660 16-Apr-1958 11:34 M-.&#16879;&#16880; ~GM-1^J
 -rwxr-xr-x   0   0 2206786690  2-Nov-1908 23:07 ~GM-9&#16890;&#16891;.&#16892;
 -r-xr-xr-x   0   0 2296679816 29-May-1912 12:00 &#16900;&#16901; ~F^J
 -rwxr-xr-x   0   0 2743657634  2-Nov-1924 23:08 ~H~Y&#16922;&#16923;.&#16924;
 -r-xr-xr-x   0   0 2296688008 29-May-1912 16:00 &#16932;&#16933; M-&^J
 -rwxr-xr-x   0   0 2206852226  3-Nov-1908 23:07 ~HM-9&#16954;&#16955;.&#16956;
 -r-xr-xr-x   0   0 2313457033 30-Nov-1911 12:00 &#16964;&#16965; ~F^J
 -rwxr-xr-x   0   0 2743723170  3-Nov-1924 23:08 ~I~Y&#16986;&#16987;.&#16988;
 -r-xr-xr-x   0   0 2313465225 30-Nov-1911 16:00 &#16996;&#16997; M-&^J
 -rwxr-xr-x   0   0 2206917762  4-Nov-1908 23:07 ~IM-9&#17018;&#17019;.&#17020;
```


what are those non recognized characters? and the chinese ones? How do I make them recognizable?

Sometimes I get:
```

 -r-xr-xr-x   0   0 2167845940 14-Dec-1933 10:41 7M-36~A8M-36~A.9M-36
 -r-xr-xr-x   0   0 2167846194 12-Aug-1934 10:41 5M-46~A6M-46~A.7M-46
 -r-xr-xr-x   0   0 2167846448 20-Aug-1934 10:41 3M-56~A4M-56~A.5M-56
 -r-xr-xr-x   0   0 2167846456 18-Dec-1934 10:41 1M-66~A2M-66~A.3M-66
 -r-xr-xr-x   0   0 2167846710 16-Aug-1935 10:41 9M-66~A0M-76~A.1M-76
 -r-xr-xr-x   0   0 2167846964 14-Dec-1935 10:41 7M-76~A8M-76~A.9M-76
 -r-xr-xr-x   0   0 2167847218 12-Aug-1936 10:41 5M-86~A6M-86~A.7M-86
 -r-xr-xr-x   0   0 2167847472 20-Aug-1936 10:41 3M-96~A4M-96~A.5M-96
```

Is that relevant for my search of a txt file with a password on it?

Sometimes I get what looks like readable names, all in caps:
```

dr-xr-xr-x   0   0 1405897813  7-Jan-1908 04:06 LAS LAN.TE^J
 dr-xr-xr-x   0   0 2152027201 31-Dec-1941 06:29 KLIRO K.IN~@
 dr-xr-xr-x   0   0 1481200512  9-Feb-2024 11:30 SK~@SJE~@S.IZ^J
 dr-xr-xr-x   0   0 1378702159 14-Jan-1908 04:30 OS-THIEU.TH~@
 dr-xr-xr-x   0   0 1229935445 19-Jan-2021 10:58 S-CIEUC~@.SIO
 -rwxr-xr-x   0   0 1229343052 20-Oct-2016 04:26 IMULTANE.OUS
 drwxr-xr-x   0   0 1330138185 17-Oct-2022 11:10 GU IMA~@.SIL
```

clarification would be thanked.

**and then I get to cluster 1569090, which is the directory I am looking for, where the file I need is located:**

```

 -rwxr-xr-x   0   0     21213 25-Mar-2017 02:34 Volumes.odt
 -rwxr-xr-x   0   0         0  5-Oct-2014 23:07 .~lock.HDD.odt#
 -rwxr-xr-x   0   0      1991 15-Dec-2014 00:38 APs working
 -rwxr-xr-x   0   0        86 19-Jan-2017 20:41 ssd
 -rwxr-xr-x   0   0       521 12-Feb-2017 13:27 luks 0.5%
 -rwxr-xr-x   0   0     18089 25-Feb-2017 01:01 dvd copying.odt
 -rwxr-xr-x   0   0       443 26-Feb-2017 22:33 computing
 -rwxr-xr-x   0   0        17 31-Mar-2017 00:14 network settings
```

all these files are in the directory I need. But the file itself is not listed. What other commands can I use to try and locate the file I need, which must be in cluster 1569090, or near it,in the same directory?

---

### Post by dragonfly41 on 2017-09-03
Bundled with testdisk is another recovery utility - photorec.
This is launched by running the command ...
```
photorec
```

You can narrow down your search pattern by configuring photorec to only look for files with extension txt (if your passwords are in a textfile).

[https://unix.stackexchange.com/questions/139531/searching-for-a-specific-file-with-testdisk](https://unix.stackexchange.com/questions/139531/searching-for-a-specific-file-with-testdisk).

If that doesn't work for you start trying other tools.

R-Linux is installed from Ubuntu Software Centre.

```
sudo apt-get install rlinux
```

Then if that doesn't help move on to try others ..

[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

If you can specify a pattern inside a file (such as a password you do remember in the passwords list) you can try forensic slicing tools.

---

