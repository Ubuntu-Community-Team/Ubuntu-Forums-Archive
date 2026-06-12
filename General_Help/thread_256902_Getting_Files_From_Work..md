---
title: "Getting Files From Work."
date: 2006-09-13
forum: General Help
---

### Post by simoncoul on 2006-09-13
I run Ubuntu at my work, and microsoft at home(as the other people is my house don't care for something different and fun).   Anyhow I was woundering if there is a program that I can get so I can install in on my windows machine and be able to retrieve my files from work on ubuntu?   

Also if it did so without interferring with the windows computer(so if someone is using it) that would be best like a quick background file transfer.   Mostly just small test documents and some power points is all I need to transfer.

Thanks

---

### Post by skymt on 2006-09-13
[COLOR="Silver"]Install openssh-server in Ubuntu, and get [WinSCP](http://winscp.net/eng/index.php) for your home box.[/COLOR]

EDIT: Oops! I read backwards! Okay, I'm looking for something that works the other way.

EDIT 2: Okay, use [this HOWTO](http://www.digitalmediaminute.com/article/1487/setting-up-a-sftp-server-on-windows) to set up SFTP on Windows, and install gftp on Ubuntu.

---

### Post by szf on 2006-09-13
Look into the capabilities of [SSH Tunneling]("http://www.google.com/url?sa=U&start=4&q=http://www.infosecwriters.com/text_resources/pdf/ssh_tunneling.pdf&e=9797&sig=___ZAElyT3nDFOCdtW9JF4M04rW6U=") (google.com cached PDF).

Do make sure that you accept the burden of doing this sort of thing - you could get frogmarched out the door of your work.

---

### Post by simoncoul on 2006-09-13
Thank you for the help I will give it a try.

---

