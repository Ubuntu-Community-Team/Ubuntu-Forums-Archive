---
title: "Perl"
date: 2007-07-13
forum: General Help
---

### Post by sasanf on 2007-07-13
I've been trying to install File::Scan::ClamAV using CPAN.  From a terminal, I enter the command sudo -MCPAN -e shell and get into the CPAN terminal (Initially I was asked if I wanted to configure manually.  I said no.  Automatic configuration took place.)  I enter the comman Install File::Scan::ClamAV, hit enter, and wait and wait and wait and wait.  I have a 3 meg connection.  It seems that File::Scan::ClamAV is nowhere to be found.  CPAN checks a lot of FTP sites and doesn't find it.  I doubt it isn't available; what is wrong with my Perl and how do I fix it.  I'm trying to install the perl module because ASSP needs it.

---

### Post by geraldm on 2007-07-13
Manual download from cpan looks like it works.  
Possibly the name is not exactly the same?
File::Scan::ClamAV  search returns File-Scan-ClamAV-1.8
Gerald

---

### Post by Mr. C. on 2007-07-14
I'm guessing the mirror is timing out.  Try another mirror

MrC

---

### Post by sasanf on 2007-07-17
Should I configure CPAN manually?  If so, how do I restart the configuration process?  I have configured it manually before, and I have all the programs it asks for except ncptftp (if memory serves me correctly, ncptftp is the name of the program it wants.  I couldn't install it when I tried to install it with apt-get and I also didn't find it when I did a search via synaptic.).

I'll try File::Scan::ClamAV-1.8

Thanks for all of the help thus far.

---

### Post by Mr. C. on 2007-07-17
No need to reconfigure - just set the urllist variable.

Start cpan

```
# cpan
o conf urllist
    urllist           
        0 [http://www.perl.com/CPAN]
Type 'o conf' to view all configuration items

```

will list the urllist.  Set it with your favorite mirror:

```
o conf urllist [http://www.perl.com/CPAN]
```

and then

```
commit
```

and retry.  You can use get information about the package with:

```
i File::Scan::ClamAV
```

and then install with

```
install File::Scan::ClamAV
```

MrC

---

### Post by Robvdl on 2008-06-14
To anyone still reading this post, at current File::Scan::Clam will not compile on Hardy, because Clam is too new. I found a workaround here that fixes this:

[http://www.asspsmtp.org/wiki/File-Scan-ClamAV](http://www.asspsmtp.org/wiki/File-Scan-ClamAV)

Check the section at the bottom: Difficulty Installing File::Scan::ClamAV 1.8

---

