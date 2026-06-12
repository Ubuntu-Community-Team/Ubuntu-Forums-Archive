---
title: "Building menus to launch apps"
date: 2007-12-11
forum: General Help
---

### Post by bentonian on 2007-12-11
I'm building my Fluxbox menus manually. How do I know what is the correct command to launch an app? Some are straightforward, just use what's in /usr/bin/, but others, like VLC, are more mysterious. Is there an easy way to find out? Thanks!

---

### Post by Emerzen on 2007-12-11
the executable for VLC is in /usr/bin, so I'm not sure what's not working for you.  I'm not a Fluxbox user, so I don't know how it works.  But in GNOME/KDE there's a way to add items to the menu, which just requires that you browse to the executable and select it.  In Ubuntu/Gnome it's under System-->Preferences-->MainMenu.  The application that does this is 'alacarte' which you can grab from the repo's.  I don't know if it will work in Fluxbox though.

---

### Post by bentonian on 2007-12-11
Fluxbox menus are build with the syntax (*App name*) {*App command*}.

I am sure I had tried 'vlc' in the menu, and it hadn't worked... Sorry for the unnecessary post.

But I was also confused because I had to use 'wxvlc' when I wanted to associate a file type to VLC under Gnome. What is the difference between the two commands?

---

### Post by Emerzen on 2007-12-11
I'm hoping my response gets your post some attention from more experienced users.  I know VLC has different skins that can be applied, on of which uses the wxwidgets toolset.

By the way, when you add a menu command such as 
vlc
to the menu, what happens when you try to use it?  What error message are you getting?

---

### Post by mcduck on 2007-12-11
You can find out the executable of a program using the 'which' command.

For example, 'which firefox' will return '/usr/bin/firefox'

(Actually I just tried and both 'vlc' and 'wxvlc' start VLC on my machine. both /usr/bin/wxvlc and /usr/bin/svlc are just symbolic links pointing to /usr/bin/vlc)

---

