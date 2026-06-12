---
title: "gFTP install problem"
date: 2005-10-20
forum: General Help
---

### Post by Baf on 2005-10-20
Hi, I have been having problems trying to get and install gFTP through sudo apt-get install ftp. I think I messed something up when I tried to add extra repos. I did it wrong at first, well typo, but even sudo apt-get update wasn't working. Its fine now, but I still have this problem with gFTP. 

This is what I get:
> steve@1234:~$ sudo apt-get install gftp
Reading package lists... Done
Building dependency tree... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  gftp: Depends: gftp-gtk (= 2.0.18-10) but it is not going to be installed
        Depends: gftp-text (= 2.0.18-10) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

I'm not sure about that apt-get -f install. I get this error in other commands too.

---

### Post by Kyral on 2005-10-20
Mind pasting your /etc/apt/sources.list here?

---

### Post by Baf on 2005-10-20
Ahhh, fixed! :) 

I guess I did do something wrong with the repos. Thats my guess anyway. I had a broken package, so it wouldn't let me update my system. I went to remove thru the broken filter in Synaptic and it was the gFTP package. 

I took that off completely then updated my system and then ran sudo apt-get update and then tried sudo apt-get install gftp. It worked. I had made a typo when I added extra repos to the sources.list I think, that is probably what did it. 

Thanks anyway though. Love the promptness!

---

### Post by dtfinch on 2005-10-20
I've never really liked gFTP. It crashes very often, but very unpredictably so. Simply saying "it crashes" is an unacceptable level of detail for bug reporting, and its stability has not improved since Warty.

---

