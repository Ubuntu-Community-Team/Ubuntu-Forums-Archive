---
title: "Connection on other pc - similar to teamviewer"
date: 2016-09-13
forum: General Help
---

### Post by sed_faster on 2016-09-13
HEllo everyone,

Usually I use teamviewer for help my friend in their pc's. But I read about teamviwer which the system has a fault security, in passwords and broadcast which use to connect between pc's. What alternatives have I to enter on pc of my colleagues and help them?

The environment is Ubuntu or Lubuntu in version 16.04 LTS

Thanks

---

### Post by TheFu on 2016-09-13
I've never seen or used teamviewer.

You can share terminal sessions with [tmux and screen]("https://www.howtoforge.com/sharing-terminal-sessions-with-tmux-and-screen") or [x2go]("http://wiki.x2go.org/doku.php/doc:usage:desktop-sharing") has a view-only mode. Both require a good level of trust between you and the other person.  For family members, I usually setup an account so I can handle issues through an ssh session - they don't usually care how, just want it fixed.  Plus, with ssh there isn't anything I can't do from 1 room or around the world on their box.

Another option is a completely non-secure presentation tool like [http://talky.io](http://talky.io).  Just use chromium or chrome and visit that website - it needs webrtc working, which requires a few odd things like a microphone and webcam. Control can be passed back and forth.  When I want the other person to learn, I think this is the better answer, since they will need to type everything.

There are probably other ways.

---

