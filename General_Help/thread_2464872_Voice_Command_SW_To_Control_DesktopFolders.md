---
title: "Voice Command SW To Control Desktop/Folders?"
date: 2021-07-14
forum: General Help
---

### Post by johnsmoke on 2021-07-14
Having issue with RSI (repetitive stress injury) lately. I tried searching but am coming up short. Running Ubuntu 20.04 - is there any voice command software to allow me to open browsers, open and close folders etc.?

---

### Post by grahammechanical on 2021-07-14
Could you list the software you have investigated and rejected? It would help us to avoid going down the same blind alleys. A brief internet search shows that there are several options for speech recognition but hardly any for voice command.

Gnome has a screen reader application called Orca but that is coming at this matter from the wrong direction. What I have found does not seem to be an easy to implement solution.

> Use a service like Alexa or Google Assistant as a voice-command utility  for Linux through the Triggercmd service. Triggercmd runs on your  computer; [use it to invoke]("https://www.freeyourdesktop.com/2019/02/voice-control-linux-using-alexa-or-google-assistant/")  Alexa or Google Assistant and have those tools execute specific Bash  scripts based on your command. Say something like, "OK Google, ask  trigger command to open the calculator." Google Assistant serves as an  intermediary with Triggercmd to run the Bash script specified by the  phrase "open the calculator."

[https://www.lifewire.com/state-of-linux-voice-recognition-2204883](https://www.lifewire.com/state-of-linux-voice-recognition-2204883)

But if you only want to execute a few commands it might be worth the effort. I imagine that trying to turn Linux completely over to voice control would be a time consuming activity.

Perhaps someone else on this forum could provide a template for a Bash script that can be used to open and close a web browser. You could then modify it as you need to.

Regards

---

### Post by dragonfly41 on 2021-07-14
As I suggested in a nearby thread discussing "tools for elders"
the Albert launcher provides a good degree of abstraction from the underlying complexity.
[https://albertlauncher.github.io/](https://albertlauncher.github.io/)

It can't be much easier to use by the non technical user.
But does need technical support to choose/configure/write the python extensions.

Your "triggers" to launch actions can be very short.  Just a few characters.

---

### Post by HermanAB on 2021-07-15
If you really have a serious accessability problem, then you should switch to Apple.

---

### Post by TheFu on 2021-07-15
Repetitive tasks can be automated.  Best NOT to use a GUI for those.  

Of my thousands of tasks, only 1 needs an actual mouse-click.  That single task took me about 30 hours to perfect.  It runs once a week for about 10 minutes and requires setup to ensure the button it presses is exactly in the correct place on the screen or it will fail.

Scripting commonly performed tasks means you can place those scripts on your desktop or in a ~/bin/ directory and run them either with a few keystrokes or with a double-click of the mouse.  Once you have those scripts setup, then you could add some sort of voice control to run each.  

[https://www.youtube.com/watch?v=WQ3LdaIpg4Y](https://www.youtube.com/watch?v=WQ3LdaIpg4Y) shows an example that sorta works, but probably not to the level anyone you find too useful.
Many of the voice-to-text engines send the voice to amazon or google for conversion, so we get to feed those data engines and lose some privacy. A few years ago, I looked into voice control for a media center on a raspberry pi Linux computer.  
[https://www.raspberrypi.org/blog/talk-to-your-raspberry-pi-hackspace-36/](https://www.raspberrypi.org/blog/talk-to-your-raspberry-pi-hackspace-36/)
[https://tutorials-raspberrypi.com/build-raspberry-pi-voice-control-for-home-automation/](https://tutorials-raspberrypi.com/build-raspberry-pi-voice-control-for-home-automation/)
You'll want the correct type of microphone.

This is very much like "I want Sandy" or "pi@hz.com" procmail handlers.  Basically, those both accepted commands on the email subject line, then carried out the command using a huge "case" statement for the understood verbs.  This is just as much about training the human as it is training the commands.
music --> play --> boston
music --> play --> the ramones
music --> pause
music --> resume
music --> next
music --> close
files --> find --> directory --> .config / vlc --> delete
files --> close
weather --> today
weather --> London
weather --> close

Basically, every verb we'd like would need to programmed to accept or locate an object to act upon.  Consistency won't be fun to ensure.  Any you'll want to setup a keyword to wake up the listening for the command - like how alexis is used on amazon products, but you can make it something funny and personal or embarrassing.  Voice training for all the possible background noise won't be easy.

---

