---
title: "Installation Not Seeing Files"
date: 2020-09-14
forum: General Help
---

### Post by greatoffender on 2020-09-14
Not the best title but I struggled with something that would make sense.

I have installed CyberGhost on Ubuntu Cinnamon before just days ago but  had to reload Ubuntu and now I can't figure this out??? The setup  couldn't be easier - create and download the configuration files, unzip  in new folder and then run *sudo openvpn --config [path to opvn file]. *When  you download the configuration file it is a zip that contains 4 files.  Place them in a folder together. All the files are in the same folder  and to avoid any typos I just dragged the opvn file in, removed the  quotes and hit Enter. Problem is that I receive an error every time  saying that the it cannot find the the other 3 files that are in the  folder with it? I did this in 2 minutes the first time I installed but  now no love. Any ideas?

Options error: --ca fails with 'ca.crt': No such file or directory (errno=2)
Options error: --cert fails with 'client.crt': No such file or directory (errno=2)
Mon Sep 14 19:03:22 2020 us=521057 WARNING: cannot stat file 'client.key': No such file or directory (errno=2)
Options error: --key fails with 'client.key': No such file or directory (errno=2)
Options error: Please correct these errors.

---

### Post by CelticWarrior on 2020-09-14
You must be in the same folder. Dragging the file to the terminal informs of its path - therefore it works (for that file) - but it doesn't change the path you're in. The command you're running expects to find the missing files in the same folder you're in, not in the same folder where the dragged file is.

---

### Post by TheFu on 2020-09-14
or
in every config file, simply specify the full path the any other files, not a relative path.
It would be easier to the cd into the directory and run the command. A 2 line scrip can make this easier.

I have no clue about the program mentioned , but it seems just like every normal, standard openvpn set I've seen.

---

### Post by greatoffender on 2020-09-14
Your right and THANK YOU. Windows apparently didn't like sharing space on my laptop with Linux so I just went all in. After 20+ years of starting and stopping I am finally going to give it a chance. There was actually an easier way to do this through the network manager but I want to use the Terminal as much as possible.

Thanks again!

---

