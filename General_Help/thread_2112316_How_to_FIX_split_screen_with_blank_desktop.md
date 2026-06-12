---
title: "How to FIX split screen with blank desktop"
date: 2013-02-04
forum: General Help
---

### Post by acpuma9 on 2013-02-04
I have been having a problem for a few days now where I start up my PC, everyting looks fine up to where I have to log in.

I get a log in screen, but the screen is split in two, as soon as I log in I get a blank desktop which is also split in two.
I cannot access any monitor or system settings at all. 

Im running Ubuntu 12.10  x64


Any advice on how to fix this because its really frustrating and it is preventing me from using my computer.

_**Please see attached image.**_

[https://mail-attachment.googleusercontent.com/attachment/u/0/?ui=2&ik=56e3ef337b&view=att&th=13ca607f43ff418b&attid=0.1&disp=inline&safe=1&zw&saduie=AG9B_P8cpJgnLg_ngqE18GuOf3Dp&sadet=1359995664589&sads=_l8cYhNK_Yvb2STtHRohpQeHkd0](https://mail-attachment.googleusercontent.com/attachment/u/0/?ui=2&ik=56e3ef337b&view=att&th=13ca607f43ff418b&attid=0.1&disp=inline&safe=1&zw&saduie=AG9B_P8cpJgnLg_ngqE18GuOf3Dp&sadet=1359995664589&sads=_l8cYhNK_Yvb2STtHRohpQeHkd0)

---

### Post by zero2xiii on 2013-02-04
Hay,

Please elaborate on the graphics set up of the system. eg, are you running nvidia graphics, what drivers are you using, proprietary or open source, version. etc.

IF you are running nvidia's proprietary drivers, after log in hit ctrl+alt+F1 (or from a rescue shell) and run the following commands:

```
sudo nvidia-xconfig
```
this should reconfigure the nvidia device in the xconfig. Just for incase there is something in there that is not right.

You might also try

```
sudo nvidia-smi -r
```

This should reset your cards, if a double buffer ECC (if I remember correctly) error is what is causing the screen split. This might not be relevant for your card.

If all the above is irrelevant, please post the output of:
```
dmesg
cat /etc/X11/xorg.conf
```

You can get this by doing (from a console as stated above):
```
echo "=================DMESG=================" > trouble.txt
dmesg >> trouble.txt
echo ""
echo "=================X11-xORG=================" >> trouble.txt
cat /etc/X11/xorg.conf >> trouble.txt
```

And copy paste the file trouble.txt's content here (it will be found in the home directory of the user logged in in the terminal)
--you can also find the path by asking 'pwd' in terminal, this will print the working directory where the file will be/was created--

If the above is not viable, you can paste to pastebin directly by doing the following steps in terminal
```
sudo apt-get install pastebinit
cat trouble.txt | pastebinit
```

and then giving us the the generated URL eg:
[http://pastebin.com/f5c9dc0b1](http://pastebin.com/f5c9dc0b1) 


Cherz and good luck :)

---

