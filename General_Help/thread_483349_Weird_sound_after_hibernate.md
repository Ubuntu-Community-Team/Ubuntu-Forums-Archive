---
title: "Weird sound after hibernate"
date: 2007-06-24
forum: General Help
---

### Post by herrma29 on 2007-06-24
I recently did a clean install of feisty on my computer. Since then, I've noticed a weird noise after waking up from hibernate that I never noticed before. It sounds like a siren and plays for a few seconds. Does anyone know what this is and/or how I can turn it off?

Thanks,
Chris

---

### Post by katja on 2007-08-13
I have this problem, too - the siren plays as the log-in screen comes up after hibernation; after I log in, I get a message that HAL failed to hibernate, though I'm pretty sure my laptop's hibernating fine - no other problems.  Does anyone know why this happens/how to get rid of the sound?  Thank you :).

---

### Post by nacy_4_u on 2007-08-21
Another solution friends (if previous wont work ..)

Friends it just simple step ..
1. hibernate your system with pcm ,master ,line-in turn to mute 
         It can be done by double clickin on sound icon on panel there mute all button .

2. When u wake up from hibernate ..
        Double click on sound icon again and turn them to unmute .

                     It will work ( it did for me )

Another solution firends (if previous dont work)

1. Hibernate your system normally .
2. When you want sound , double click on sound icon on panel and mute all channel like master,pcm ,line-in everythin .
3. Set your systen to suspend(by single right clicking on icon ) from Battery icon (for laptops), desktop can choose other normal way.
       suspending sysem takes around 50 seconds (not a big task )
4. Recover from suspend after few seconds and again open volume control(ctrl+O) and unmute all channels (pcm,master)
5. Play your music player and get sound back ..

                   This will surely work as it workd on more than 10 diffrent config system 
                                          for any further querry in dis contact me on  gmail - [email]nacky4u@gmail.com[/email] / [email]nacky_4_u@yahoo.com[/email]

[B]

---

### Post by katja on 2007-08-21
thanks :).

I think I found an easier way, though - after looking through my system a couple of days ago, I figured out that the sound was this one: /usr/share/gnome-power-manager/gpm-suspend-failure.wav, and that to disable it I can un-check the "use sound to notify in the event of an error" box in "Power Management Preferences: General;" so far, i haven't heard it again :).

---

