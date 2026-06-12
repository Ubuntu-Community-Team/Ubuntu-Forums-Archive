---
title: "Something wrong with this script."
date: 2013-06-03
forum: General Help
---

### Post by sorrensen on 2013-06-03
So I have a 64-bit Ubuntu 12.14 VDS and i'm accessing it through PuTTY and I have the Shell Script to install a Garry's Mod Server:
```

#!/bin/bash
echo "Garry's Mod Installer"
echo "A screen may ask you to agree, just type yes when this happens!"
echo "Starting in five seconds!"
sleep 5
echo "Installing lib32gcc1 just incase it is missing"
apt-get install -y lib32gcc1
echo "Downloading HLDSupdatetool"
wget http://www.steampowered.com/download/hldsupdatetool.bin
chmod +x hldsupdatetool.bin
./hldsupdatetool.bin &lt;&lt;&lt; "yes"
./steam
echo "Downloading CSS"
./steam -command update -game "Counter-Strike Source" -dir . -verify_all
echo "Downloading Garry's Mod"
./steam -command update -game garrysmod -dir . -verify_all
echo "Installed! Will continue with setup in 5 seconds."
sleep 5
echo "Copying CStrike folder to orangebox for CSS content."
cp -r ./css/cstrike ./orangebox
echo "Done!"


```[SIZE=2][FONT=arial]

[/FONT][/SIZE]I removed line 11 because it gave me this error:

```
[SIZE=2]./install.sh: line 11: syntax error near unexpected token `;&'[/SIZE]
[SIZE=2]./install.sh: line 11: `./hldsupdatetool.bin &lt;&lt;&lt; "yes"'[/SIZE]
```

And now It's not saying ./steam is a directory and It's not creating files or anything do I need to give it permission to, or something else please help! It's been a month and I still haven't got this server set up :(.

---

### Post by sorrensen on 2013-06-03
```

Downloading CSS
./install.sh: line 12: ./steam: No such file or directory
Downloading Garry's Mod
./install.sh: line 14: ./steam: No such file or directory
Installed! Will continue with setup in 5 seconds.
Copying CStrike folder to orangebox for CSS content.
cp: cannot stat `./css/cstrike': No such file or directory
Done!

```

---

### Post by sorrensen on 2013-06-04
I found a somewhat solution for other people but it does not work for me because it's the first thing I did after getting my VDS provider to change my OS to 64-bit because I couldn't install ib32gcc1 on a 32-bit system :\ 
[http://forums.steampowered.com/forums/showthread.php?t=1984105](http://forums.steampowered.com/forums/showthread.php?t=1984105)
apparently worked for other people.

---

### Post by steeldriver on 2013-06-04
It looks like you downloaded the script as html and some html codes got left in

```
./hldsupdatetool.bin [COLOR=#ff0000]**&lt;&lt;&lt;**[/COLOR] "yes"
```

should probably be

```
./hldsupdatetool.bin [COLOR=#ff0000]**<<<**[/COLOR] "yes"
```

(a bash 'here string'). There may be other issues as well - try downloading it again.

I remember your other thread - I still don't understand why you changed to a 64-bit OS so that you could install lib32gcc1... and then install a 32-bit application - lib32gcc1 should NOT have been needed if you'd stuck to 32-bit

---

### Post by Buah on 2013-06-04
> I remember your other thread - I still don't understand why you changed  to a 64-bit OS so that you could install lib32gcc1... and then install a  32-bit application - lib32gcc1 should NOT have been needed if you'd  stuck to 32-bit

As far as I know, Source dedicated server (srcds) which [**[COLOR=#000000]sorrensen[/COLOR]**]("http://ubuntuforums.org/member.php?u=1824329") is installing, has partial multithreading support so with 64-bit os srcds runs little better.

---

### Post by sorrensen on 2013-06-04
The script wasn't downloaded it was made over putty then I just copied and pasted the codes off of this site: [http://tigerclan.net/blog/2012/10/24/how-to-set-up-a-garrys-mod-13-server-in-ubuntu/](http://tigerclan.net/blog/2012/10/24/how-to-set-up-a-garrys-mod-13-server-in-ubuntu/)
Yes well it seemed everyone else could ge[COLOR=#000000]t[/COLOR][COLOR=#000000] lib32gcc1 on a 32-bit system but I couldn't and apparently srcds needs it.
Ill try:
```
[/COLOR][COLOR=#000000][FONT=Ubuntu Mono]./hldsupdatetool.bin [/FONT][/COLOR][COLOR=#ff0000][FONT=Ubuntu Mono]**<<<**[/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono] "yes"
```[/FONT][/COLOR]

---

### Post by sorrensen on 2013-06-05
> **steeldriver said:**
> It looks like you downloaded the script as html and some html codes got left in

```
./hldsupdatetool.bin [COLOR=#ff0000]**&lt;&lt;&lt;**[/COLOR] "yes"
```

should probably be

```
./hldsupdatetool.bin [COLOR=#ff0000]**<<<**[/COLOR] "yes"
```

(a bash 'here string'). There may be other issues as well - try downloading it again.

I remember your other thread - I still don't understand why you changed to a 64-bit OS so that you could install lib32gcc1... and then install a 32-bit application - lib32gcc1 should NOT have been needed if you'd stuck to 32-bit

hldsupdatetool.bin [COLOR=#ff0000]**<<<**[/COLOR] "yes" worked thanks so much!

---

