---
title: "having some serious issues"
date: 2015-10-12
forum: General Help
---

### Post by Atzel on 2015-10-12
Hello ubuntu community!
My pc crashed a few weaks ago and now my girlfriend and me have to use a laptop of her brother with ubuntu installed. The problem is, that im used to use windows for years and i have not the time nor then nerves to get into ubuntu as an operational system. I dont want to be offensive, but as long as i tried to make it working somehow, more and more questions came to my mind that just nobody can explain me in the internet in a way to understand it.
I need your help, guys with the brains to understand that mess.

Soo the big problem is, that nothing works. apturl doesnt work. i cant load nor install any package. there is no ubuntu software center installed. i tried to reinstall but i failed.

now that firefox seems to be installed, i tried to find a way to enable apturl in firefox but the easiest description i got is this one:

[h=3]Firefox versions up to 3.0[/h] (Works without installed Gnome libraries) 
 
[LIST]
[*] Type about:config into the Location Bar (address bar) and press Enter.
[*] Right-click -> New -> Boolean -> Name: **network.protocol-handler.external.foo** -> Value -> **true** (Replace *foo* with the protocol you're specifying)
[*] Right-click -> New -> String -> Name: **network.protocol-handler.app.foo** -> Value -> **/path/to/app** (Replace *foo* with the protocol you're specifying and */path/to/app* with the path to the application you want to run)
[*] Ensure [network.protocol-handler.expose-all]("http://kb.mozillazine.org/Network.protocol-handler.expose-all") is set to **true**.
[/LIST]


Now, pls someone explain me what i have to insert as foo. i dont know which protocol im specifying (do i have to insert "firefox"? isnt that a browser? whats a protocol? what does it look like?)

I really dont know what to do. 

All we can do is watching videos on youtube or streamcloud, nothing else works. you cant play games, because not one single game is running anyhow. and i love plaing games (hell do i).
not even an emulator is working. you cant execute any exe, it just doesnt work. i tried to do it with vine....but that just slowed the pc heavily down, triing to emulate a 2d sidescrolling jump n run. the laptop isnt even able to get the resolution done.

One day i had to print some formulars. Guess what: nothing works alone.

Pls someone tell me in particular what i have to do just to get the apturl working and reinstall ubuntu software center.

Have a nice day

---

### Post by nknwn on 2015-10-12
open the Terminal (command box). Try to Install the Ubuntu software centre with this command:
[B]sudo apt-get install software-center

[/B]You will be prompted to enter your password**. **There is no feedback in the terminal until you press enter.

---

### Post by grahammechanical on 2015-10-12
Let me see if I understand the situation. Your Windows machine crashed and you cannot use it anymore. Correct? You are now using someone else's machine that has Ubuntu on it and you are experiencing some problems because you do not know how to do things. Correct? Can I give you a wild guess?

That laptop has an out of life (unsupported) version of Ubuntu on it. When the OS loads you should see a splash screen that will tell you the version of Ubuntu. You say you have Firefox 3.0. Do you mean Firefox 30? The latest version of Ubuntu has Firefox 41.0 So, if you really have Firefox 3.0 then you must also have a very, very old version of Ubuntu that must surely be out of life.

Of course, Windows exe files do not run in Linux. Those programs are not written to run in the Linux OS in the same way that Linux programs are not written to run on the Windows OS. The program called Wine has a certain value for running Windows applications in Linux but the value is limited because the Wine developers do not have the access to information about how Windows works. My advice would be not to try to run Windows games in Linux but to run Linux games instead. Or, get your Windows machine repaired if you cannot live without Windows games. That loptop might not be powerful enough to run games anyway.

Instructions on how to do things in Linux often give examples that contain the word "foo." When we write the command we substitute the word "foo" with the actual name of the library or application. So the instruction that you quote states "replace foo with the protocol that you are specifing and /path/to/app with the path to the application you want to run."  For example,

```
sudo apt-get install foo
```

When running the actual command we substitute the word "foo" with the complete name of the application which may not be the same as the name it is known by. Applications and libraries are called packages in Linux because they have been packaged by a Package Manager. 

Why don't you tell us what you want to do? And just one task at a time and we may be able to tell you how to do it. At the moment I have no idea of what you want to do or even it it is sensible to try. Please also tell us the hardware specifications of the machine and the version of Ubuntu that is on it. 

And please remove the offensive comments. We have a code of conduct on this forum and although you may not have read the code of conduct you have agreed to comply with it by the fact of registering on the forum. Frustration is not a justifcation for being bad mannered. It prevents me from giving assistance.

---

