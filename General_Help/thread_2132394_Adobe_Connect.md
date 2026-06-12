---
title: "Adobe Connect"
date: 2013-04-04
forum: General Help
---

### Post by lunalui on 2013-04-04
Hi everyone, sorry to open yet another thread on this subject, but I do hope someone here is able and willing to lend a hand. I need to have Connect Add-in up and running for a work video conference in two weeks. Unfortunately I seem unable to make it work. 
I installed the Connect add-in without any problem and the connection test looked fine. Unfortunately, when connecting to the room, the Adobe Connect window was stuck with this message "loading adobe connect". Nonetheless, after a wile I had the choice to open another room. If I tried and opened a second room, the connection seemed fine only that it behaved as the add-in was not installed (I did have incoming sound and video but it was impossible to turn the microphone on). Also, the room audio configuration applet suggests that I should install connect add-in. If I agree the window/tab just shuts down.
Inspired by this closed thread [http://ubuntuforums.org/showthread.php?t=1466276&highlight=adobe+connect](http://ubuntuforums.org/showthread.php?t=1466276&highlight=adobe+connect)
I installed flashplugin-installer (which removed adobe-flash_properties-gtk and adobe-flashplugin)
The result is that now instead of getting a "loading adobe connect" page I get a blank one and I need to open several rooms before one does load and when it does the problem is the same.

This happens on my 32 bit ubuntu 12.04 (with fallback desktop) with similar behaviours on both firefox 19.0.2 and Chromium on a vaio laptop VPC-YA1C. 

with many thanks in advance for your replies

---

### Post by Irihapeti on 2013-04-04
I've tried to use Adobe Connect on Ubuntu 12.04 without success.

If you don't need to share your desktop (i.e. present videos, presentations etc that are on your machine), then you don't need it. Just using ordinary Flash Player works fine, though the machine will use a lot of CPU (and get warm).

If you do need to share your desktop, you are probably better off using Windows. I have a suspicion that Flash runs more efficiently under Windows and therefore doesn't heat the PC so much.

---

### Post by lunalui on 2013-04-05
Thanks for your reply. The point is, I'll only take part in the meeting and it's not me who choose the settings. In fact, it looks like connect add-in does open a window but this window is just blank, and the meeting room is missing. I'm adding some screen captures, in case it may be helpful. 
This is the connect add-in blank page:
[IMG]https://lh3.googleusercontent.com/-jPftAyoZVv4/UV7fdxt1hNI/AAAAAAAAAWE/TgXfrZgFoQQ/w826-h435-p-o/fenetre.png[/IMG]
If I click on the blank page, the word "settings" appears, but I cannot do anything with it.
On the other hand, if I keep opening rooms (ie blank pages) after a while a room is opened "outside" add-in and in the initial window
[IMG]https://lh6.googleusercontent.com/-P6oj04vuRO4/UV7fhPTzhzI/AAAAAAAAAWM/Fe1iJ4n7oYQ/w822-h435-p-o/reunion.png[/IMG] 


However I cannot start the audio server because the host requires connect add-in. I click on "install add-in" and I end up with yet another blank window

[IMG]https://lh6.googleusercontent.com/-gD25_u_Ir1s/UV7fkTj-7aI/AAAAAAAAAWU/75SntyvXePU/w812-h428-p-o/final.png[/IMG]

anyway, thanks again.


PS Windows is not an option for me: basically I've never use it and I'm pretty happy about that.

---

### Post by Azdour on 2013-04-05
Hi,

I had lots of problems when I tried to use Adobe Connect on Ubuntu 10.04 (which the docs say is the only version they support, not sure if that is true or not). This is from memory so I apologise in advance if I get things wrong and just to say that while I got the add-on to start I had no sound and the microphone did not work...:

1. I had to go into my flash settings via the browser:
[http://www.macromedia.com/support/documentation/en/flashplayer/help/settings_manager.html#117118](http://www.macromedia.com/support/documentation/en/flashplayer/help/settings_manager.html#117118)

2. You need to access the various settings to allow the microphone and camera to be accessed from the URL that is the meeting place. You also need to set up the Web Privacy to always allow from the URL that is the meeting place.

For me that allowed the add-on to start but I got no further.

---

### Post by Irihapeti on 2013-04-05
I had a very similar experience to what's in the screenshots. I tried all sorts of things (even asked on the Adobe Connect forums - now closed) and got nowhere.

However, if you aren't a presenter or organiser, it's unlikely that you'll be asked to share your desktop, which is the only reason you would need the addin as opposed to ordinary Flash player.

In that case, remove the Connect Addin and just install Flash player, which is what I did.

I attended a few meetings with Ubuntu 12.04. I was able to take part in conversations without difficulty. We didn't use webcams, so I'm not sure how that would have worked.

---

### Post by lunalui on 2013-04-05
Hi, 
thanks a lot for your replies. 

Azdour, I've fiddled around with the settings, but it hasn't improved things. The add-in opens a window which is empty and that's it :(

Irihapeti, thanks for the suggestion, I have flash player already installed. The problem is that the settings of the site I connect to do not allow me to start my audio without add-in (in fact, I'll try this again, but I'm pretty sure that the same settings won't even allow me to open a room, if they detect that add-in is not installed). As a consequence, I can listen to what other people say, and we can see each other, but they won't be hearing me. 

again thanks a lot for your suggestions

---

### Post by lunalui on 2013-04-05
OK, so I've tested removing the add-in and connecting: I can access the conference room, but the audio problem remains the same (so actually, this means that in my second picture the access is actually via flash player).

---

### Post by Irihapeti on 2013-04-05
From what I remember about it (it was nearly a year ago), the facilitator/tech support person had specifically to enable participants' microphone access. It wasn't available automatically.

Maybe the same will apply to your meeting. It might be worthwhile contacting your facilitator ahead of time and asking.

---

### Post by lunalui on 2013-04-06
Already done that. He knows that he can allow my microphone by changing the settings (we tested that) but he's not willing to do so, because he says this will limit the functionalities for the other participants too. :x ](*,)

---

### Post by Irihapeti on 2013-04-06
That is indeed frustrating. Unfortunately, I don't have any other suggestions. We can only hope that someone else comes up with something.

---

### Post by lunalui on 2013-04-06
no worries and thanks a lot for all your suggestions: the people on this forum rock! :)

---

