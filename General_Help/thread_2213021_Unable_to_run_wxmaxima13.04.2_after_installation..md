---
title: "Unable to run wxmaxima13.04.2 after installation."
date: 2014-03-24
forum: General Help
---

### Post by arroy_0209 on 2014-03-24
I am using ubuntu 12.04.4 and recently tried to install wxmaxima after downloading the latest version in gzipped-tar compressed form. The instaructions I have followed are from: [https://help.ubuntu.com/community/wxMaxima](https://help.ubuntu.com/community/wxMaxima). The commands I had used successively are as follows: (please note that I had not used the "apt-get remove" command initially since I did not have an older version already installed)
```

sudo apt-get install build-essential checkinstall
tar xfvz /"locationof"/wxMaxima-"latest-version".tar.gz
sudo apt-get build-dep wxmaxima
cd /"locationof"/wxMaxima-"latest-version"/
./configure --enable-dnd --enable-printing --enable-unicode-glyphs --prefix=/usr --exec-prefix=/usr
make 
sudo checkinstall

```
I have used proper path for "locationof" above. I am not very sure about correctness of what I did next: There was a prompt on the terminal: 
"Please write a description for the package. End your description with an empty line or EOF." followed by ">>" sign where I just copied the sentence as suggested in the webpage: "wxMaxima is a cross platform GUI for the computer algebra system maxima based on wxWidgets." and on successive >> prompts, typed 0 and then ENTER and my email address again as suggested. Hopefully these steps were more-or-less ok since ultimately the debian package was created and this is suppesed to be auto-installed to give me operative wxmaxima package. Finally when I use the command "wxmaxima" on the terminal, the expected window opens but the problem is no operation can be done. Each time I give some mathematical problem to solve, I get the error message: "Not connected to Maxima!" What had gone wrong and what do I do about it?

---

### Post by arroy_0209 on 2014-03-24
I have solved the problem myself after consulting some websites.

---

### Post by Guaicuru on 2014-07-30
> **arroy_0209 said:**
> I have solved the problem myself after consulting some websites.

I have similar problems and couldn't get wxmaxima to run.
Would you please write where did you find the solution?
Thanks.

---

