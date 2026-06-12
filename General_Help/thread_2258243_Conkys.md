---
title: "Conkys"
date: 2014-12-26
forum: General Help
---

### Post by wtwrestling07 on 2014-12-26
[COLOR=#000000]i just installed ubuntu about 3 days ago and im just now starting to get the hang of it and i want to install a conky on the right hand side of my screen and i am following the instructions exactly the way it says [/COLOR][https://help.ubuntu.com/community/SettingUpConky](https://help.ubuntu.com/community/SettingUpConky)[COLOR=#000000] to get it to stay on on screen on the right hand side except its not working. I installed conky, curl, lm sensors, and hddtemp. I created the .conkyrc file in home directory and copyed the conky.config file from the etc/conky/conky.config to the .conkyrc file in the home directory. Only editing i did to the file was changed it from "top_left" to top_right" and i even tryed just leaving it normal and i cant get it to start on start up or stay on my home screen. I did the [/COLOR][COLOR=#333333][FONT=UbuntuMono]killall -SIGUSR1 conky and also added the Conky to start up applications with Conky as the name and conky as the command and i still get nothing on start up. After i created the .conkyrc file when i try to start the conky from the terminal by typing conky i get this error message.

[/FONT][/COLOR][COLOR=#000000]Conky: invalid configuration file '/home/michael/.conkyrc'[/COLOR]


[COLOR=#000000]Conky: missing text block in configuration; exiting[/COLOR]
[COLOR=#000000]***** Imlib2 Developer Warning ***** :[/COLOR]
[COLOR=#000000]This program is calling the Imlib call:[/COLOR]


[COLOR=#000000]imlib_context_free();[/COLOR]


[COLOR=#000000]With the parameter:[/COLOR]


[COLOR=#000000]context[/COLOR]


[COLOR=#000000]being NULL. Please fix your program.[/COLOR]


[COLOR=#000000]i dont know what i am missing. or how to fix. i also tryed copy and pasting a few custom ones from this forum and still nothing. any suggestions?[/COLOR]

---

### Post by deadflowr on 2014-12-26
Post the conkyrc here.
Please use [code tags]("http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168")

---

### Post by vasa1 on 2014-12-26
@deadflowr, OP wrote:> I created the .conkyrc file in home directory and copyed the conky.config file from the etc/conky/conky.config to the .conkyrc file in the home directory. Only editing i did to the file was changed it from "top_left" to top_right" and i even tryed just leaving it normal and i cant get it to start on start up or stay on my home screen.So that's the .conkyrc. Maybe OP needs to shift the conky window down a bit so as not to conflict with Unity's top bar?

---

### Post by deadflowr on 2014-12-26
> **vasa1 said:**
> @deadflowr, OP wrote:So that's the .conkyrc. Maybe OP needs to shift the conky window down a bit so as not to conflict with Unity's top bar?

I wonder why they would have installed curl, lm-sensors and hddtemp, if they only copied the conky from /etc.
There is nothing in the /etc conky that uses any of those.
At least, not without adding to it.

Anyway the only usual way conky conflicts with unity's panel is when it's launched at Ubuntu's startup( something do to with how unity starts; which can normally be fixed by delaying conky)
The output posted is usually indicative of something messed up in the conkyrc. Perhaps the OP inadvertently added a letter to something, or erased something by accident.
Usual clue
> Conky: missing text block in configuration; exiting

---

### Post by wtwrestling07 on 2014-12-28
> **deadflowr said:**
> I wonder why they would have installed curl, lm-sensors and hddtemp, if they only copied the conky from /etc.
There is nothing in the /etc conky that uses any of those.

 

i installed them because i read on the offical conky install page they will be usefull for conky. idk if i need them or not to be honest. i can get conky to run if i dont make the .conkyrc folder aned just type conky in terminal. only thing is as soon as i create the .conkyrc folder and copy the config file and killall to get it to start runnning from the .conkyrc folder i get an error message saying 

Conky: invalid configuration file '/home/michael/.conkyrc'


Conky: missing text block in configuration; exiting
***** Imlib2 Developer Warning ***** :
	This program is calling the Imlib call:


	imlib_context_free();


	With the parameter:


	context


	being NULL. Please fix your program.

ive never installed a conky before and ive only had ubuntu for about a week maybe few days less than a week.

---

### Post by deadflowr on 2014-12-28
.conkyrc is a file only, no folder involved.
you could try a simple copy
```
cp /etc/conky/conky.conf ~/.conkyrc
```
which will copy the contents directly into the .conkyrc file.

---

### Post by NM5TF on 2014-12-28
@wtwrestling07

could you please post your .conkyrc file here as asked by DeadFlower ???

we can't help if we don't know what you are using.....

from your error message it shows that it crashes as soon as it calls the lmlib, or the libraries for lm-sensors....

I suspect it is trying to call whatever was setup in the original .conkyrc file that you just copy/pasted from
some web site.....but we can't know that for certain unless you show us your .conkyrc file...it needs to be
configured so it calls YOUR hardware specifically.....

for a self-proclaimed newcomer to Ubuntu & possibly *nix in general, Conky can be a little ambitious
to say the least...that said, excellent help is available on these forums....

and once understood to a degree, Conky can produce some dazzling desktop eye-candy...

here is a screenshot of my current desktop....2 seperate Conky's running simultaneously....

---

