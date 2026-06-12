---
title: "[SOLVED] Netbeans 6 installation problem"
date: 2008-01-14
forum: General Help
---

### Post by Balt603 on 2008-01-14
Hi, 
      I was trying to get Netbeans 6 installed today on Feisty and I seem to have hit a serious brick wall. Got Java 1.6 working fine, so I downloaded the Netbeans installer, made it executable and ran it. The installation process seemed to run fine, but when it finished I was left with no desktop icon and no menu entries...no way to start the program.

So I searched for all the Netbeans threads and found the installed directory of the file and that I could run it from the command line using "netbeans". This results in:

```

The program 'netbeans' is currently not installed.  You can install it by typing:
sudo apt-get install netbeans5.5
Make sure you have the 'multiverse' component enabled
bash: netbeans: command not found

```

I've been searching these forums and googling for about an hour and haven't found how to get it running. The only possible clue I've found is that when I ran the .sh installer I shouldn't have run it under "sudo" (which I did...seemed logicial). Which makes me think that maybe I should uninstall and reinstall as a local user, but not sure how to accomplish that. There is only one unanswered post on that topic :-)

If anyone can give me a hand I'd be grateful.... as should be obvious, I'm one of the hoard of ex-windows users whose linux tinkering ability is limited :-)

---

### Post by Balt603 on 2008-01-18
Wow, nobody's got anything on this? That's a new one on me....

---

### Post by KevMeistr on 2008-01-18
Hey...

I installed sun-java6 from the synaptic package manager that comes with Feisty and then I downloaded Netbeans 6 from the net... the file was about 167 mb and mine worked fine...
Try searching on google for "netbeans + 167 mb + glassfish"...my netbeans came with glassfish v2 which is some kind of editor for java...

now I've got a new problem.. the electricity went out and now its telling me that they can't find apt-get package installed.

---

### Post by kellemes on 2008-01-18
Have you tried "sudo netbeans"?? This gives you root-privileges you may need..

also try..
```
sudo updatedb
sudo locate netbeans
```See what it comes up with.. netbeans must be somewhere if it's installed correctly.

---

### Post by Balt603 on 2008-01-18
Thanks for the advice guys. I actually figured out how to get the uninstall script going and ran that, which seemed to work...unfortunately it automatically took out java as well. As soon as I get that, I'll try redownloading the installer and this time installing it under my local user rather than root (seems often suggested)

---

### Post by r-mo on 2008-01-18
The Netbeans-6.0 installer doesn't install into your path.  So to run it use (by default)
```
/usr/local/netbeans-6.0/bin/netbeans
```

---

### Post by Balt603 on 2008-01-18
Undoubtely r-mo's solution would be a good workaround, but I solved mine by a simple uninstall, then reinstall WITHOUT root. Now running fine. Thanks for the replies.

---

