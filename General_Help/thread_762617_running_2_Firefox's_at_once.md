---
title: "running 2 Firefox's at once"
date: 2008-04-22
forum: General Help
---

### Post by MemoryDump on 2008-04-22
hey there,

I'm running Firefox 3.0Beta 5 on my system. (Hardy)
What I'd like to do is run 2 copies of Firefox at the same time.
Why?
Well, my wife is at home using the computer.. and me I'm at work connected via a NX session. This prevents me from running the same firefox profile she is on. I know about the profileselector, however I'd like to be able to prevent from using that. Can't we both "share" the same profile?

or could I load a new firefox using another user's account on my system? (ex: ~otheruser/.mozilla/otherprofile.something

"firefox -no-remote" doesn't seem to work.

thanks
-MD

---

### Post by yaknowwat on 2008-04-22
firefox -P <profilename> --no-remote

works but is incomplete because you cannot attach to it again aka 

you can't do firefox -P default --no-remote twice and get two windows for the same user it'll say to close firefox.

but you can do firefox -P user1 --no-remote then firefox -P user2 --no-remote

running firefox with a special variable design may be the best solution.

but what it seems you are trying to do is network the profile just so that you are aware this is potentionally dangerous as it can cause corruption if you two are using it at the same time and you two would overwrite each other.

though all you have to do is create a symbolic link to your wife's home computer.

I suggest using a profile linking technique.

~/.mozilla/firefox/f4t54gr.profilenet/ -> yourwifes-network-firefox-profile/

then make a link firefox -P profilenet --no-remote

and it would access your wifes computer for the profile if it can't load it because your not connected to your wife then it may possibly restart the profile and you'll have to redo the symbolic link (so backup that link)

---

