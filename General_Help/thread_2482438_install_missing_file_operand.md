---
title: "install: missing file operand"
date: 2022-12-30
forum: General Help
---

### Post by lekarlos33 on 2022-12-30
Hello,

Im trying to install some executables (bitcoin core) in /usr/local/bin and when using the ''install'' command I get a ''missing file operand'' error. Not sure what to do since Ive used this command over and over and many ubuntu installations without any problems. the /usr/local/bin directory does exist I checked.Here's my terminal :

truenym@truenym-2tb:~/install/bitcoincore/bitcoin-24.0.1/bin$ sudo install -m 0755 -o root -g root -t /usr/local/bin
install: missing file operand
Try 'install --help' for more information.


Not sure how to proceed

---

### Post by HermanAB on 2022-12-31
Look at your command.  You list a zoo of options but with no file to install. So the error message is specific and correct.

---

