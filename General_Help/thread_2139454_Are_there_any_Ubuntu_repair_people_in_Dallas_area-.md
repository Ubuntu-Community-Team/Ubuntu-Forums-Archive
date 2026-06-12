---
title: "Are there any Ubuntu repair people in Dallas area--will pay"
date: 2013-04-26
forum: General Help
---

### Post by dell49 on 2013-04-26
Update manager tells me that it "Failed to load the package list" and that "This is a serious problem. Try again later. If this problem appears again, please report an error to the developers." I have tried this repeatedly, after full shutdowns and restarts--same result.

Details are: 
 
"E:Unable to parse package file /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_universe_i8n_Translation-en(1), E:Problem opening /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_raring_updates_main_binary-amd64_Packages, E:The package lists or status file could not be parsed or opened."

Machine is a Toshiba Portege R-835 running 64-bit Ubuntu 12.10. What happened is that, as I was, by the invitation, downloading 13.04 ringtail, the computer crashed. Have been having problems with the apport reporting bug and user/bin/signon-ui has been blocking shutdown. Oh, and the red circle with the white bar in the middle is showing in the top bar, and when clicked, says that the details above "usually means that your installed packages have unmet dependencies".

I had been hoping that ringtail would 'fix,' by replacement, the apport and signon files that had turned problematical. Instead, I now seem to have a permanently unchangeable installation. At this point, this probably is beyond my meager capabilities. Are there any skilled 'repair people' in the Dallas metro area? I'll pay! Or is this installation now defunct?

---

### Post by tgalati4 on 2013-04-26
Open at terminal:

```
sudo apt-get check
sudo apt-get clean
sudo apt-get update
sudo apt-get dist-upgrade
```

See how far you get.

I normally find that it's quicker to create a Live USB of the distro of choice and do a clean install.  Repairing can be time consuming and you never know what else is broken.  What caused the computer to crash in the first place?

---

### Post by ibjsb4 on 2013-04-26
In terminal:

```
sudo rm -r /var/lib/apt/lists/*
sudo mkdir /var/lib/apt/lists/partial
sudo apt-get update
```

And that should fix it

And welcome back :)

---

### Post by dell49 on 2013-04-26
tgalati4 and ibjsb4: Thanks much!

But one question: do I do each in turn, hitting enter after each (as I'm guessing), or the whole lot?

(Want to get it right!)

---

### Post by ibjsb4 on 2013-04-27
One line at a time.

---

