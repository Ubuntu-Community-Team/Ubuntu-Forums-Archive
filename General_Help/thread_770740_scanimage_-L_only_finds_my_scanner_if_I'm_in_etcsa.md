---
title: "scanimage -L only finds my scanner if I'm in /etc/sane.d?!?"
date: 2008-04-27
forum: General Help
---

### Post by chewtoy on 2008-04-27
I'm trying to hook my Epson Perfection 1670 up to my Ubuntu Dapper box.  Eventually, the goal is to let multiple users scan documents from various computers on the network (through phpSANE, or something else?) but for now I'll settle for getting the scanner working locally :).

I followed the instructions [here]("http://ubuntuforums.org/archive/index.php/t-26911.html") and got the firmware file installed and the /etc/sane.d/snapscan.conf edits done, but could only ever get **scanimage -L** to detect my scanner intermittently.  **xsane** never detects it.

But then I stumbled onto the problem:

**scanimage -L** only detects my scanner ***when the working directory in my shell is /etc/sane.d*** :confused:

The above is true whether I'm logged in as root or as a normal user.  Note that when I'm in /etc/sane.d and the scanner is detected, it seems that scanning via scanimage works fine (although I haven't played with any options yet).  As I said, xsane never detects the scanner, but for now I assume it's all the same problem as above.

This is one of those true WTF moments I occasionally have when toddling around in Ubuntu.  Can anyone give me any insight?

---

