---
title: "wget and progress bar"
date: 2012-12-14
forum: General Help
---

### Post by spiralciric on 2012-12-14
Hello, I was wondering if you can help me with this. I have googled for an hour and found other people's solutions that just don't work.
I need to get all files from a web directory and display a progress bar with zenity. Thus the code looks like this:

```
sudo wget -r --no-parent http://www.somewebsite/directory/ -P /somelocaldirectory/
```I have tried pipeing to zenity progress bar, but that only shows 0 and 100%. I have tried several versions with sed, but they dont work at all.

Thanks

---

### Post by Habitual on 2012-12-14
why sudo?

```

function my_wget()
{
var3=%$(wget -r --no-parent http://www.somewebsite/directory/ -P /somelocaldirectory/)
}

touch /tmp/$$
(  ( echo 1 ; while [ -f /tmp/$$ ] ; do sleep 1 ; done ; echo 100 ) |  zenity --progress --pulsate --auto-close --text="Counting Snapshots..."  --width=150 --title="" --undecorated --no-buttons) & my_wget
rm /tmp/$$
```I ripped this snippet from a yad-driven program. Yad is the successor to 
zenity and has more options. :)

Good Luck.

Edit0:
My code came from one, or more of these:
[A Little Hacking game with bash and Zenity - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=1598617") 
 [A complete zenity dialog examples 1 » Linux by Examples]("http://linux.byexamples.com/archives/259/a-complete-zenity-dialog-examples-1/") 
 [Choose profile before launching GNOME Terminal emulator [bash] [shell] [gnome] [zenity]]("http://snippets.dzone.com/posts/show/4572") 
 [Bash Scripts using Zenity - FedoraForum.org]("http://www.forums.fedoraforum.org/showthread.php?t=191603") 
 [Zenity Manual]("http://library.gnome.org/users/zenity/stable/")  
[zenity site:unix.com/shell-programming-scripting/ - Google Search]("http://www.google.com/search?source=ig&hl=en&rlz=1G1GGLQ_ENUS241&q=zenity+site%3Aunix.com%2Fshell-programming-scripting%2F&aq=f&aqi=&aql=&oq=")
[Ubuntu Forums - Threads Tagged with zenity]("http://ubuntuforums.org/tags.php?tag=zenity") 
 [Zenity and newlines in entry dialog. - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=892039")  
[Zenity Progress Window]("http://gnome-look.org/content/show.php/Watcher+--+Zenity+Progress+Window?content=104818") 
 [YAD &#8212; A fork of zenity with more features « TechnoStripe]("http://technostripe.com/yad-a-fork-of-zenity-with-more-features/#more-450")
[zenity - Google Search]("http://www.google.com/cse?cx=016212844476379046035%3A5cta2rjlwko&ie=UTF-8&q=zenity&sa=Search&siteurl=www.ig.gmodules.com%2Fgadgets%2Fifr%3Fexp_rpc_js%3D1%26exp_track_js%3D1%26url%3Dhttp%253A%252F%252Fwww.google.com%252Fcse%252Fapi%252F016212844476379046035%252Fcse%252F5cta2rjlwko%252Fgadget%26container%3Dig%26view%3Ddefault%26lang%3Den%26country%3DUS%26sanitize%3D0%26v%3D758c0d2355d83eb6%26parent%3Dhttp%3A%2F%2Fwww.google.com%26libs%3Dcore%3Acore.io%3Acore.iglegacy%3Aauth-refresh%26is_signedin%3D1%26synd%3Dig%26mid%3D23%23st%3Dc%253Dig%2526e%253DAPu7icr37q4oOkwX6oLduZTFir9pEQMlaroJFy1FZ4scSGAoy4v%2F0LEqA3WSiJ0gvN38%2FhKQxJAGQRjP8ALeYq582qCkN4YO%2FXxLo2L5yXTa4Am3sj8BQagu5TA%25252BPY%25252BiTm6lDZbSWN4C%26gadgetId%3D104172544382452133415%26gadgetOwner%3D104433570538816626367%26gadgetViewer%3D104433570538816626367%26rpctoken%3D-121511455%26ifpctok%3D-121511455")
["if [ "$?" -eq "0" ]" +zenity - Google Search]("http://www.google.com/search?num=100&hl=en&rlz=1G1GGLQ_ENUS241&q=%22if+%5B+%22%24%3F%22+-eq+%220%22+%5D%22+%2Bzenity&aq=f&aqi=&aql=f&oq=")
[zenity progress via function example]("http://linux.byexamples.com/archives/265/a-complete-zenity-dialog-examples-2/")  [Advanced Application Launchers With Zenity - TildeHash]("http://www.tildehash.com/?article=advanced-application-shortcuts-with-zenity")

---

### Post by spiralciric on 2012-12-16
Unfortunately, this code does not work :(, zenity gui does not appear at all. Thanks for the links, I will try with yad as well.

---

### Post by Habitual on 2012-12-20
Let me break down the process here, so maybe you'll understand what I presented:

What needs to happen is a progress-meter needs to be shown while the "wget" action is performed. So you do a touch /tmp/$$ in the script and zenity is told
"while [ -f /tmp/$$ ]" (while file exists) ; do the pulse action, then remove /tmp/$$ and continue with the 
written code.

so when you say things like "doesn't work" or "other people's solutions that just don't work", it doesn't say to much. 
The meat-and-potatoes of the operation and should be tried out solo on your host is:
 ```
zenity --progress --pulsate --text="Progress-bar Check"  --width=150 --title="" --undecorated --no-buttons

```You never answered my question:
Why sudo?

Post your script using[noparse]```

```[/noparse] tags.
Thank you,

---

### Post by spiralciric on 2012-12-20
Ok, I will try this again.
Sudo because I need to save files inside /etc/somefolder

---

### Post by Habitual on 2012-12-20
[QUOTE=]Sudo because I need to save files inside /etc/somefolder[/QUOTE]

fair enough. Script should also include a "sudo -k" option to discard temporary sudo privs. It's good security practice to do so.

Anyways: after reviewing [http://linux.die.net/man/1/zenity](http://linux.die.net/man/1/zenity) the code that should work on your host may be:
```
zenity --progress --text="Progress-bar Check"  --width=150 --title="" 
```

yad has more options, as you can tell.

---

