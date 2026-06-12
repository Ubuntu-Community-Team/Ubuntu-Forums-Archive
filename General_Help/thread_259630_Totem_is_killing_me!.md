---
title: "Totem is killing me!"
date: 2006-09-17
forum: General Help
---

### Post by Average Joe on 2006-09-17
I have been trying really hard (I think) to get Totem playing all kinds of multimedia types. It mostly fails. However, I have installed mplayer-686 and mozilla-mplayer and at least now I can play some movies etc.

However, when browsing the internet, I cannot see any movies because those are still associated with Totem. For instance, a test page for wmv files at  [http://www.vdat.com/techsupport/windowstest.asp]("http://www.vdat.com/techsupport/windowstest.asp") gives me an error "Totem could not play 'fd://0'."

And YES, I have installed all the gstreamer (good, bad, ugly, whatever) codecs and the w32codecs package. It just doesn't work.

So how can I associate the multimedia files in Firefox with Mplayer instead?  My first thought was Edit > Preferences > Downloads > Download Actions. But it is not there.

Uninstalling the useless Totem gives me a message that the ubuntu-desktop will be uninstalled as well. OK, that doesn't sound to well, so skip it.](*,)

Could somebody out there please explain me if it is possible at all to view  avi and/or wmv files on the internet, or do I just have to reboot in Windows to see them?:confused:

---

### Post by marianom on 2006-09-17
Correct me if I'm wrong but they're two different subjects. If you download a movie to your PC you can use Totem to play it. It doesn't mean that all embed content in a web page will be played by Totem. For that you still need the browser plugin.
Anyway, I tried the page you suggested -my firefox didn't supported it- so I looked for the embed url, copied it to totem and played it with success (it's horrible slow, I have to say).

I recall using EasyUbuntu ([http://easyubuntu.freecontrib.org/](http://easyubuntu.freecontrib.org/)) and Automatix ([http://www.getautomatix.com/](http://www.getautomatix.com/)) to install most of these codecs.
Did you try them?

Good luck

---

### Post by nix4me on 2006-09-17
That video plays fine with my setup.  I have Totem-xine with w32 codecs and the totem-firefox plugin.

nix4me

---

### Post by AndyCooll on 2006-09-17
Easiest way is to follow marianom's suggestion and use Easy Ubuntu or Automatix to get mplayer to be your default Firefox multimedia plugin.

Not sure if it's true, but I've heard some apps need mozplugger to work properly with FF.

Finally, you shouldn't ever need to uninstall Totem, just the totem-xine-firefox-plugin.

:cool:

---

### Post by Average Joe on 2006-09-18
Thanks for your messages. Currently I am running totem-gstreamer. Maybe I should try totem-xine instead. I think I have the browser plugins installed correctly. I remember I had some compatibility issues when I tried to switch totem-gstreamer to totem-xine before.

I am aware that I could copy and paste the url in totem, but I find that too much of a hassle when just to watch a movie on a website (maybe I am just lazy). Besides, I never got it to work with the mms protocol (not even with the gstreamer-mms plugin).

I am just interested in the browser integration part. I hardly have any movies on my hard disk anyway. But when it comes to multimedia, Firefox gives me more error messages than my Windows OS ever did.

Maybe I should give Automatix a try. Honestly, I don't like it too much, since it doesn't really show what is being installed exeactly on your computer. And there is no undo. Everytime I start it, the boxes that I had checked before are unchecked again. Does that mean it is not on my system anymore? No, but this implies that when I do want to get rid of it, I am on my own (like checking the repository boxes in Synaptic).

But I will give totem-xine another try, that is, when I get back from work.:)

---

### Post by Average Joe on 2006-09-18
I tried the totem-xine and the totem-xine-firefox-plugin and it worked!  Thanks nix4me =D>! Now I can watch movies on the internet with Firefox.

To get sound with flv video's (e.g. Google Video) I had to do:
```
sudo ln -s /tmp/.esd-1000 /tmp/.esd
```
That's kind of strange 'hack' to me, but at least it works.

Still no sound when playing local flv video's with totem though. But with mplayer it works fine. Any suggestions?

---

