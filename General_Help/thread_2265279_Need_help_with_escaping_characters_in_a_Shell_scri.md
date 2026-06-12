---
title: "Need help with escaping characters in a Shell script :/"
date: 2015-02-13
forum: General Help
---

### Post by Maxunit on 2015-02-13
Dear Ubuntu Community,

I hope you can help me. I am lost at escaping characters properly within a shell script. WINE is needed to run the Software and usually the Windows Counterpart to start the Software looks like this:

> CAGGameServer-Win32-Shipping.exe cag_p?PlanetManagerName="FUNTOWN"?adminpassword=thisisnttherealpassword?steamsockets?Port=7777?PeerPort=7778?QueryPort=27015?MaxPlayers=32?CloudDir="Cloud"?ServerName="My Cool home server" -seekfreeloadingserver

Now the quotation mark parts cause problems. How would I have to change the entire thing, so that the quotation marks and the words in it are parsed properly by the shell script?

Cheers,

Maxunit

---

### Post by yetimon_64 on 2015-02-13
To escape a special character in bash try placing a backslash before the character.

eg "My Cool home server" becomes My\ Cool\ home\ server. Doing this will escape the spaces without the use of quotation marks, do the same before each question mark or any other such characters if they cause problems (eg, ? becomes \? and so on for all other such characters that cause problems for bash).

Edit: I am assuming it is a bash script (eg a shebang line of #!/bin/bash at the top of the script) this may vary if another shell interpreter is used.

---

### Post by Maxunit on 2015-02-13
Thanks, yetimon_64.

The Bash Script looks like this right now:

> #!/bin/bash
wine CAGGameServer-Win32-Shipping.exe cag_p?PlanetManagerName=\"FUNTOWN\"?adminpassword=thisisnttherealpassword?steamsockets?Port=7777?PeerPort=7778?QueryPort=27015?MaxPlayers=32?CloudDir=\"Cloud1\"?ServerName=\"My\ Cool\ home\ server\"?gamepassword=test -seekfreeloadingserver

and causes errors, like this (from the log):

> [0006.32] Log: UCloudStorageBase::QueryForCloudDocuments ..\..\CAGGame\\"Cloud1\"?ServerName=\"My\

I am slightly clueless at all, since another workaround worked with another Game Server Software around 2 years ago, but it had a completely different bash script.

---

### Post by yetimon_64 on 2015-02-13
No you don't escape the " marks, you delete them totally and escape (\) the spaces. Delete the " marks and try again with the escape marks left as is.  The "FUNTOWN" entry should work with the quotes without being escaped as it has no spaces in the name. It is the spaces you need to specifically escape in bash, some other symbols like ! may need to be escaped at times as well. Good luck.

---

### Post by Maxunit on 2015-02-13
Ah okay, I will try that.

EDIT:

I deleted the " marks for "My Cool home server" and added the \ instead. It results in:

> [0006.31] Log: UCloudStorageBase::QueryForCloudDocuments ..\..\CAGGame\Cloud1?ServerName=My\

EDIT 2:

Sorry if I sound dumb. Linux is still a bit confusing for me if it comes to such stuff :/

EDIT 3:

Adding a \ before the ? does nothing.

---

### Post by yetimon_64 on 2015-02-13
> "My Cool home server" becomes My\ Cool\ home\ server. 

 Please post the actual script content that is now causing the problem I think you may now be doubling up on escape marks and need to see what you have now set it up as.

Edit ? marks may be OK, some symbols don't need to be escaped.

---

### Post by Maxunit on 2015-02-13
Here it is:

> #!/bin/bash
wine CAGGameServer-Win32-Shipping.exe cag_p?PlanetManagerName="FUNTOWN"?adminpassword=thisisnttherealpassword?steamsockets?Port=7777?PeerPort=7778?QueryPort=27015?MaxPlayers=32?CloudDir="Cloud1"?ServerName=My\ Cool\ home\?gamepassword=test -seekfreeloadingserver

I tried adding \'s before the ?'s and it made no difference.

EDIT:

It seems to ignore the " behind Cloud1 and continues to use the rest of the line o_O

---

### Post by yetimon_64 on 2015-02-13
```
#!/bin/bash
wine CAGGameServer-Win32-Shipping.exe  cag_p?PlanetManagerName="FUNTOWN"?adminpassword=thisisnttherealpassword?steamsockets?Port=7777?PeerPort=7778?QueryPort=27015?MaxPlayers=32?CloudDir="C   loud1"?ServerName=My\ Cool\ home\ **server**?gamepassword=painiscupcake  -seekfreeloadingserver                      
``` Note what I added in bolded type. I would also suggest opening a terminal (bash) and running the command with variations of the escape sequences until you get it working from terminal. Then when you get the syntax correct try in the bash script again. Nothing other than the name is sticking out at the moment, will keep looking at it for a bit to see if something stands out.

 Note: please use code boxes for code, there seems to be unusual gaps when I've copied your output to my editor, I corrected a couple but there are still some there.

eg > ```
CloudDir="C   loud1"
```

Edit: I should have noted pressing the # button in the Advanced editor is how to put code tags around highlighted text/code.

---

### Post by Maxunit on 2015-02-13
Hmm whatever I did so far, did nothing. It always continues to parse some characters after ```
?CloudDir="Cloud1"
```

---

### Post by yetimon_64 on 2015-02-13
May be best to wait for more experienced helpers here OP. I am not overly familiar with the wine command syntax, specifically all those ? marks, and can't spot a problem as such. Hopefully someone will pop in soon to help out.

Good luck. yeti.

---

### Post by Maxunit on 2015-02-13
Thanks for helping nonetheless, yeti :)

---

### Post by nerdtron on 2015-02-13
Haven't taken time to read everything you did so far but have you tried enclosing everything using single quotes? Something like this:

```
wine cgagamer.exe 'This is the part where you put anything..including \, or ? or * or $ or [space] or " or anything and it will be treated as literal' 
```

---

### Post by Maxunit on 2015-02-13
That resulted in some kind of...debugger message? Wow, never saw such strange stuff...

---

### Post by nerdtron on 2015-02-13
Post the terminal output here including the command you run.

---

### Post by Maxunit on 2015-02-13
Command:

```
wine CAGGameServer-Win32-Shipping.exe cag_p?PlanetManagerName="FUNTOWN"?adminpassword=thisisnttherealpassword?steamsockets?Port=7777?PeerPort=7778?QueryPort=27015?MaxPlayers=32?CloudDir="Cloud1"?ServerName="My Cool Home Server"?gamepassword=painiscupcake  -seekfreeloadingserver
```

Terminal Output is huge, since it spams the console with this repeating sentence:

```
UCloudStorageBase::GetFileSizeOnDiskForDoc INVALID DOCUMENT! Idx: 3
```

which comes from this faulty command line parameter execution:

```
[0006.40] Log: UCloudStorageBase::QueryForCloudDocuments ..\..\CAGGame\Cloud1?ServerName=My\
```

It should say:

```
[0006.40] Log: UCloudStorageBase::QueryForCloudDocuments ..\..\CAGGame\Cloud1\
```

I know that the quotation parts are the issue, since I played around with it a bit and ONCE (but dont ask me how) managed to get it half-working. Instead of cluttering the console with the error message, it remained rather silent, but created the Folder "Cloud_" instead of "Cloud1" (without the "). If the "FUNTOWN" and "Cloud1" are accepted properly, the Server usually creates a folder called "Cloud1_FUNTOWN_*namehere*"

---

### Post by nerdtron on 2015-02-13
Where did you put the single quotes? I don't see any.

have you tried:
```

wine CAGGameServer-Win32-Shipping.exe 'cag_p?PlanetManagerName="FUNTOWN"?adminpassword=thisisnttherealpassword?steamsockets?Port=7777?PeerPort=7778?QueryPort=27015?MaxPlayers=32?CloudDir="Cloud1"?ServerName="My Cool Home Server"?gamepassword=painiscupcake'  -seekfreeloadingserver 
```

or 
```

wine CAGGameServer-Win32-Shipping.exe 'cag_p?PlanetManagerName="FUNTOWN"?adminpassword=thisisnttherealpassword?steamsockets?Port=7777?PeerPort=7778?QueryPort=27015?MaxPlayers=32?CloudDir="Cloud1"?ServerName="My Cool Home Server"?gamepassword=painiscupcake  -seekfreeloadingserver' 
```

---

### Post by Maxunit on 2015-02-13
I will try both. Also hanging around in the WINE IRC Channel asking for help. They seem to be baffled as well, since the commandline splitting seems to behave weird.

---

### Post by Maxunit on 2015-02-13
The first line you posted results in the usual error and the 2nd one outputs some really weird...stuff.

---

### Post by Maxunit on 2015-02-13
Someone from the WINE IRC had an idea which seem to have fixed it. Windows was just adding spaces before each ?, so that it looks like this:

```
wine CAGGameServer-Win32-Shipping.exe cag_p?PlanetManagerName="FUNTOWN" ?adminpassword=thisisnttherealpassword ?steamsockets ?Port=7777 ?PeerPort=7778 ?QueryPort=27015 ?MaxPlayers=32 ?CloudDir="Cloud1" ?ServerName="My Cool Home Server" ?gamepassword=painiscupcake -seekfreeloadingserver
```

---

