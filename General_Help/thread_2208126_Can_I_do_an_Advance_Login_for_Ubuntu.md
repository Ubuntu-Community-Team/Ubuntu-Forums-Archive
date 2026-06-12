---
title: "Can I do an Advance Login for Ubuntu?"
date: 2014-02-26
forum: General Help
---

### Post by claus.gaming on 2014-02-26
Okay, so I have a very simple question, and I'm sure it's a "no, this is not possible sorry bro" answer. But I'll ask anyways.

Is it possible for the log in screen for Ubuntu (or any other OS) to be customize to an advanced degree? 
For example I'd like my login screen to be a simple game, so when the game is done (by done I mean winning the game or receiving an 'x' score) that it will log you into your account.

Is this even possible? To make the log in essentially what ever you want beside typing in a password, or a fingerprint scanner, or facial recognition, could it be something more?

I can't wait for your response guys and gals.

---

### Post by ian-weisser on 2014-02-26
It's possible, if you're a good programmer with lots of time available.

Login authentication is handled by a system called PAM (Pluggable Authentication Module). You can write a game-based PAM the lives alongside fingerprint PAM and password PAM and others.

The actual login screen that uses PAM is part of lightdm. You can add a game to lightdm by downloading and changing the source code.

Not easy. Not a beginner project.

---

