---
title: "Using Xubuntu on the school computer"
date: 2007-10-10
forum: General Help
---

### Post by PmDematagoda on 2007-10-10
Ok, now before I tell my problems trying to install Xubuntu on the school computer, let me tell you that I am doing this with the authorisation of the teacher in charge of that computer who is very happy with Xubuntu:).


Now installing Xubuntu was easy but it is configuring it properly and installing the necessary programs that is the biggest obstacle especially due to the fact that the computer is completely offline which renders using the repos as useless. Now my problems:-

1) I installed Acrobat Reader 8 using it's .deb file found in the Adobe site but after installation I can't seem to find it in the Main Menu or even to try to add it to the Main Menu. Is there anyway I can find it?

2) Installing Java is too difficult especially since I have no idea about Xfce, so could anyone help me on installing Java on Xubuntu using it's .bin file?

3) How do you search for files in Xubuntu?

That is all for now, so any help on any of these questions would be greatly appreciated.

If you are wondering why I installed Xubuntu, it's because the computer has the following specs:

3.0 Ghz Celeron
256 Mb RAM
128Mb integrated Intel VGA


Anyone would agree that Xubuntu will have the best performance with such a computer. I also  would like to add that XP was installed on this computer 5 times:-P and failed miserably on all times(typical);).

---

### Post by FuturePilot on 2007-10-10
You might want to look into [APTonCD]("http://aptoncd.sourceforge.net/")
Then you can put the repos in your pocket:lol:

---

### Post by mali2297 on 2007-10-10
> **PmDematagoda said:**
> 
1) I installed Acrobat Reader 8 using it's .deb file found in the Adobe site but after installation I can't seem to find it in the Main Menu or even to try to add it to the Main Menu. Is there anyway I can find it?

The command should be *acroread*, try to type it in the terminal.

> 
2) Installing Java is too difficult especially since I have no idea about Xfce, so could anyone help me on installing Java on Xubuntu using it's .bin file?

Generally you would run
```

chmod +x filename.bin
sudo ./filename.bin

```
in the terminal.

> 
3) How do you search for files in Xubuntu?

There might be some suitable GUI tool, but I use exclusively *locate* and *find* from the command line.

---

### Post by PmDematagoda on 2007-10-10
Which search tool is best? Locate or find?

---

### Post by mali2297 on 2007-10-10
> **PmDematagoda said:**
> Which search tool is best? Locate or find?

*locate* is faster since it uses a database but *find* is more advanced. For example, it lets you restrict your search to a certain type like directory or symbolic link.

---

### Post by PmDematagoda on 2007-10-10
Hey, I have one more new problem, now when I installed Xubuntu, I partitioned one of the hard drives to be mounted along /media/storage. Now the thing is that I can't use it. How do I change the ownership of that drive?

I know it is chmod but what are the other things?

---

### Post by PmDematagoda on 2007-10-10
> **mali2297 said:**
> *locate* is faster since it uses a database but *find* is more advanced. For example, it lets you restrict your search to a certain type like directory or symbolic link.

Do you know a good guide on using find?

---

### Post by mali2297 on 2007-10-10
> **PmDematagoda said:**
> Do you know a good guide on using find?

A quick search on google about *linux command find* gave this

[http://www.hccfl.edu/pollock/Unix/FindCmd.htm](http://www.hccfl.edu/pollock/Unix/FindCmd.htm)

among many other useful results.

If you want a GUI tool, you can have a look at [catfish]("http://software.twotoasts.de/?page=catfish") (haven't tried it myself).

---

### Post by PmDematagoda on 2007-10-10
Thanks for the good guide mali2297:).

And thanks to FuturePilot for the APTonCD idea:).

And is there anyway in installing kernels on this computer?

---

### Post by PmDematagoda on 2007-10-11
Ok, now it seems that my teacher loves Xubuntu so much that his brother wants Ubuntu as well:).

So here are his questions:-

1) Does the stock Live CD have the basic necessities such as Open Office, Adobe Reader, Thunder Bird or Evolution.

2) If Ubuntu can be used properly on a laptop with 1.6Ghz Celeron, 512Mb RAM laptop.

---

### Post by mali2297 on 2007-10-11
> **PmDematagoda said:**
> 
1) Does the stock Live CD have the basic necessities such as Open Office, Adobe Reader, Thunder Bird or Evolution.

Ubuntu comes with Open Office and Evolution. Xubuntu has instead Abiword, Gnumeric and Thunderbird. Neither has Adobe Reader but Evince.

> 
2) If Ubuntu can be used properly on a laptop with 1.6Ghz Celeron, 512Mb RAM laptop.


I have similar specs and can run regular Ubuntu fine. I now have chosen XFCE over Gnome but not out of necessity.

---

### Post by PmDematagoda on 2007-10-11
I have a question myself, now the Xubuntu I installed has quite an old kernel and has a few issues concerning shutdown and restart and I want to upgrade it to Gutsy's version. How do I do this on a computer that is fully offline?

---

### Post by mali2297 on 2007-10-11
> **PmDematagoda said:**
> I have a question myself, now the Xubuntu I installed has quite an old kernel and has a few issues concerning shutdown and restart and I want to upgrade it to Gutsy's version. How do I do this on a computer that is fully offline?

See the last section here:
[https://help.ubuntu.com/community/GutsyUpgrades](https://help.ubuntu.com/community/GutsyUpgrades)

It should work with the Xubuntu alternate CD as well.

---

### Post by kadath on 2007-10-11
A good GUI frontend for the command line search tools is [Catfish]("http://software.twotoasts.de/?page=catfish"). It's in the repos. No GNOME dependencies either, so it's perfect for Xubuntu.

---

