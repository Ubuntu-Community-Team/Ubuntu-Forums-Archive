---
title: "GAH!! I've tried VLC and MPlayer... They both fail to just automatically load!"
date: 2007-06-02
forum: General Help
---

### Post by mmilitia9 on 2007-06-02
What am I doing wrong?  I've tried VLC with Firefox Plugin and MPlayer with Mozilla Plugin.

All I want in a damn media player is to just.... Open automatically and play whatever I am trying to tell it to play.  Why is this so difficult under Ubuntu?

What steps do I need to follow inorder to have everything pre-configured in Firefox to just load in an EXTERNAL  player and play?  

My problem seems to be either I can get it to load but I get it loaded in an black tab or I get it to play in Mplayer external player but doesn't have any play back options.. Or I get it to play in VLC external but VLC wont play Real/MOV and etc.. What the hecks going on? 

Can someone give me a good howto?

Thanks,

Dominick

---

### Post by jjacobs2 on 2007-06-02
Try this: in firefox open edit > preferences > content > Manage > select the file type you want to play > change action > Open them with this application > /usr/bin/gmplayer
Alternately you could set them to download to the computer there and open them manually.  Keep in mind with mplayer that there are two ways to open it.  Using gmplayer will give you graphical controls but using mplayer will only give you keyboard controls.

---

### Post by mjpoetic on 2007-06-02
Surprisingly (to myself) **[COLOR=#008000]totem-mozilla[/COLOR]** has been working well for me. *I only have had problems with trying to get a reliable player for Opera. So a miny howto would be:

 ```

 sudo apt-get install totem-mozilla
```

By the way, I have totem using the default gstreamer backend, but you can see what works better for you (**[COLOR=#008000]totem-gstreamer[/COLOR]** or **[COLOR=#008000]totem-xine[/COLOR]**).

 Also, I have heard that having multiple plugins that do the same thing may cause a problem (found that somewhere here in the forums). If you do have problems, just try to uninstall all but one and restart Firefox.

---

