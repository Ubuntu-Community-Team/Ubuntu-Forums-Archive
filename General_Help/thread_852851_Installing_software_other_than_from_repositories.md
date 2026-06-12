---
title: "Installing software other than from repositories"
date: 2008-07-08
forum: General Help
---

### Post by minhtun.it on 2008-07-08
Hi Everybody,

I'm a newbie Linux user and I'm kinda lost in finding a way to install software without using software repositories.

I've just installed Ubuntu on my computer a few days ago, and found out that I couldn't play multimedia files like MP3 and DVD discs.  I have read somewhere that I can go download and install VLC Media Player for Linux from VLC home page.  So I browsed there to download the installer package at an Internet Cafe` because I don't have Internet connection at home like most people in my country.  But what I found out there was I couldn't find any downloadable stand-alone installer package; instead, it just provides instructions to install the software from a repository which I can't do at home.

Are all software installations for Linux repository-based?  Or are there alternatives?

Looking forward to hearing from you all.
Thanx in advance,
Min Htun Zaw
Linux Newbie

---

### Post by dominiquec on 2008-07-08
I'm assuming you're familiar with Synaptic?  If not, open System->Administration->Synaptic Package Manager.

In the Synaptic Package Manager, select the files you want installed.  Then, click on File->Generate Package Download Script.  You'll need to supply your own filename for this script.

Now, go to a computer where you can run the script.  If it's any Linux computer, just run the script.  If you don't have Linux, download the files in the script manually.

Bring the files back to your home computer, and open up Synaptic again.  Click on File->Add Downloaded Packages.

---

### Post by dominiquec on 2008-07-08
By the way, you don't need to specify the packages individually when you click on File->Add Downloaded Packages.  The directory of the files will do.

---

### Post by iaculallad on 2008-07-08
There are alternatives for installing softwares in Ubuntu. Visit this [link]("http://monkeyblog.org/ubuntu/installing/"), it gives you detailed information on how to install .deb, .rpm, tarballs, .bin, and many other installation format.

---

### Post by minhtun.it on 2008-07-08
Thank u all for helping me with my problem.

---

