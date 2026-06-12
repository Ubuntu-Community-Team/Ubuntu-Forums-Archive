---
title: "Problem updating/installing Shotwell from Yorba's PPA (saucy)"
date: 2014-02-07
forum: General Help
---

### Post by AleveSicofante on 2014-02-07
I have a problem trying to update or install Shotwell from Yorba's PPA in Saucy. Here's the output in Synaptic's details:

```

(Reading database ... 206400 files and directories currently installed.)
Unpacking shotwell (from .../shotwell_0.15.1-1~saucy1_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/shotwell_0.15.1-1~saucy1_amd64.deb (--unpack):
 trying to overwrite '/usr/share/shotwell/ui/collection.ui', which is also in package shotwell-common 0.15.0-0ubuntu1
No apport report written because MaxReports is reached already
                                                              dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/shotwell_0.15.1-1~saucy1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:

```

I tried manually deleting the file /var/cache/apt/archives/shotwell_0.15.1-1~saucy1_amd64.deb to no avail.

Any help will be highly appreciated.

---

### Post by aavelor on 2014-02-15
I had the same problem and my solution was to disable Yorba's PPA from Synaptic, since I don't really care if Shotwell is up to date because I never use it. You can install Synaptic package manager fromt the software center. 

Hope this helps.

---

### Post by AleveSicofante on 2014-02-16
I actually found the solution here: [http://askubuntu.com/questions/405862/trying-to-overwrite-file-already-in-shotwell-common-package-while-installing-s](http://askubuntu.com/questions/405862/trying-to-overwrite-file-already-in-shotwell-common-package-while-installing-s)

The last answer was the simplest. I tried it and everything went fine since then.

But thanks anyway.

---

### Post by kolinab on 2014-03-22
> **AleveSicofante said:**
> I actually found the solution here: [http://askubuntu.com/questions/405862/trying-to-overwrite-file-already-in-shotwell-common-package-while-installing-s](http://askubuntu.com/questions/405862/trying-to-overwrite-file-already-in-shotwell-common-package-while-installing-s)

The last answer was the simplest. I tried it and everything went fine since then.



Thanks for the lead to that solution. Since what is the 'last' answer may change over time, here is the solution that worked for me (posted to the Ask Ubuntu link above by Avinash Raj on Jan 22):

```

[FONT=Ubuntu Mono]sudo dpkg -r shotwell-common
[/FONT][FONT=Ubuntu Mono]sudo apt-get install shotwell[/FONT][FONT=Ubuntu Mono]
[/FONT]
```

---

