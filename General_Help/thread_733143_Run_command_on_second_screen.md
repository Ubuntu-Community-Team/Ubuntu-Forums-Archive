---
title: "Run command on second screen"
date: 2008-03-23
forum: General Help
---

### Post by mystic_juju on 2008-03-23
Hi,

I am running hardy, a dual monitor setup, with nvidia drivers installed using envyNG. my second monitor acts as a separate x screen.

I've got avant-window-navigator installed (the gutsy version) and all works well, but here's my question: when i boot up, awn starts up only on my primary monitor and not on my second monitor. to run it on the second monitor i have to choose it from my applications>accessories>avant window manager on the second monitor. Then it runs fine on the second monitor too. I want to know whether there is some command i can write into my startup to run it on the second screen when things boot up.

I am asking this here and not over at AWN, since it seems like something that can apply to anything, when you want to run an application on the second x screen. Basically I just want to know whether there is some command that you can type into the terminal which will open up an application screen-specific, or whether there is some niftier way for me to do this.

I am fairly new to the whole affair, so help would be much appreciated.

---

### Post by fela on 2008-03-23
type ```
avant-window-navigator --help
``` it will display a list of options. there might be a 'display' option, that's so you can specify what X screen to use. Then if you find the option, add that to the item in System > Preferences > Sessions. (you could add 2 so that it appears on both X servers/displays)

---

### Post by mystic_juju on 2008-03-23
thanks for the reply....

running avant-window-navigator --help did bring up the additional commands i can run, one in particular being "screen=SCREEN". so, running "avant-window-navigator screen=1" from the terminal made it run on my second monitor successfully, but when I added this to the startup options (in System>Preferences>Sessions), it still wouldn't do it right from bootup. instead, it would run two instances of AWN on my primary screen. 

maybe its not recognizing that my second screen exists by the time i run it. is there some way i can delay the call to that command?

---

### Post by fela on 2008-03-23
that's funny, as it didn't bring the options on my comp...maybe my installations ******, oh well i don't use awn

this is a weird idea i just had, but did you make sure, when you added the session startup item for the second screen, that you did it on the appropriate screen? I might be talking gobbledegook but it's a brainwave i've just had (could work like that surely if there's seperate X servers?).

---

### Post by mystic_juju on 2008-03-23
well i got it running on the second monitor by adding "avant-window-navigator --screen=1" to the startup, although now it doesn't run well on the second monitor, which wasn't the case when i was doing it manually - it displays lines instead of the activated applets. gonna see if i can play around with some settings here..

---

### Post by fela on 2008-03-23
why do you want AWN on both screens anyway? If i were you i'd just leave one screen for extra space, not fill it up with docks and menus and stuff. (+ more system resources with an extra X server)

---

### Post by mystic_juju on 2008-03-23
yeah, i hear you about the extra space and that. its just that i've found having the separate x screen works the best for my dual monitor setup. other configurations just seem to act weird, since i have diff resolutions on the two screens, and don't want compiz thinking i got one really large screen. so now, because of the separate x screen, i run applications separately in the two places, hence the need for running AWN twice.

currently what i have is a pretty nice setup, and i'd rather run AWN manually on the second screen than change my setup, but obviously if i can find a way to run it automatically without hitches, then that would be best.

---

### Post by fela on 2008-03-23
maybe you could google your problem and see if anyone else has it...or you could (in the meantime maybe) make a launcher on the top gnome panel that ain't too conspicous (to keep with the mac feel) to launch awn in the right screen...just a suggestion

---

### Post by mystic_juju on 2008-03-23
yeah - gonna do some more research, see if i come up with something. good suggestion on the launcher tho - will do that for now, thanks.

---

