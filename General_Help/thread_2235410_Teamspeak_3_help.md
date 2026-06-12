---
title: "Teamspeak 3 help"
date: 2014-07-20
forum: General Help
---

### Post by mickey3 on 2014-07-20
Hey, I'm very new in using Ubuntu and I'd like to be able to talk with my friends using Teamspeak 3. I've tried Mumble and Skype on my old os but nothing really matched teamspeak 3 but I was not able to install Teamspeak 3 from the Software Centre and by downloading the files but I could not find Teamspeak 3 in the Software Centre and I ran into trouble with the file as when after I had opened the file and done all the required things in the terminal I could not open the ts3client_linux_amd64 file and I am not sure what to open to be honest.
If anybody could help me I would be so greatfull.

---

### Post by firemansphen2 on 2015-06-08
The only way I have found to run Teamspeak 3 in Ubuntu is to go to xterm and change your directory to the teamspeak 3 folder.  From there you need to run the shell script.  For me this would be how you open Teamspeak 3 after it has been installed.

```
cd Downloads/TeamSpeak3-Client-linux_amd64-3.0.16
sh ts3client_runscript.sh
```

I then renamed the folders so it would be easy to remember how to run it again like so:

```
cd Downloads/TS3 
sh TS3run.sh
```

Hope that helps!

---

### Post by Knocks on 2015-08-16
Were you running a stable build of TeamSpeak or a beta when this started happening?  I had major voice static issues with the stable release, so my only solution was to get the latest build from [TeamSpeak ]("http://www.goteamspeak.com") (not through the Software Center), and the latest beta fixed the issues.

---

