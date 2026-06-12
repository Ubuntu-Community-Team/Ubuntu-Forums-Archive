---
title: "How to login with password without pressing enter"
date: 2021-05-29
forum: General Help
---

### Post by vitalifrolov on 2021-05-29
I am running Ubuntu 20.04. Is there a way to make login easier: have Ubuntu login as soon as the password is typed in without hitting enter key?

Or alternately is where a way to add like a button for a mouse to act as an enter next to the password field ?

---

### Post by mikewhatever on 2021-05-29
...and why make it easier, when it in not hard as is? The Enter key signifies that you are done typing the passwaord and not just distracted or resting.
There is a button in the Slick Greeter, or whatever they use in Mate, so it is not impossible to add it.

---

### Post by ajgreeny on 2021-05-29
Surely moving from keyboard (entering password) to mouse (clicking on OK button) is slower and not nearly as easy as just hitting Enter; you have been typing, after all!

---

### Post by GhX6GZMB on 2021-05-29
Major logic fail here. How is the system to know when your password is complete? Passwords don't have a fixed length.

Is your Enter key defective?

---

### Post by grahammechanical on 2021-05-29
Activate the On Screen keyboard. On Ubuntu 20.04 at the login screen, top right of the screen click the icon of a human. That will bring up an accessibility menu and you can activate the On Screen keyboard and use the mouse to put in the password and press the "Enter" key.

Regards

---

### Post by TheFu on 2021-05-29
> **vitalifrolov said:**
> I am running Ubuntu 20.04. Is there a way to make login easier: have Ubuntu login as soon as the password is typed in without hitting enter key?

Or alternately is where a way to add like a button for a mouse to act as an enter next to the password field ?

The computer doesn't know what the password is or even how long it might be.  In Unix systems, there is no limitation for the length of a password.  We humans get tired around 100 characters.

The way that passwords are validated is 
[LIST=1]
[*]encrypted passwords is stored in a DB at account setup time or whenever we change the password
[*]at login, the input username and password are used in the same way that the encrypted password was stored in that DB to generate another encrypted version. It is this 2nd crypt-text that gets compared to the password DB for the specific username.  The crypt() C function is used for this.
[*]Either those two text fields match (Success!) or they do not (Fail).
[/LIST]

Linux uses crypt() hashing with a per-username "salt", combined with a per-system seed to validate passwords.  That basically means the size of the encrypted password constant, regardless of the actual password length. I've over-simplified this, since multiple different hashing methods can be used in the same passwd DB by different usernames.

If you want to know more, run  ```
man -s 5 crypt
```

Most login screens support <enter> after typing the passphrase to mean "submit".  The only places I see that NOT used is with websites that require some sort of extra validation - usually security-theater - like many bank websites have.  Their goal is to make automated attacks harder, but not cause too much hassle for real humans.  The few places that do not accept <enter> often believe that automatic mouse movement and clicking isn't possible, which is untrue. There are lots of tools which can capture both keyboard and mouse inputs for playback later.

---

### Post by coley9225 on 2021-05-29
It sounds like your asking if you can set your loggin to work like window 10 pin number. When I was using win 10, I set a pin,12345678(not the real pin, just an example). As soon as I typed the 8, it would welcome me and log into my windows, no enter button press needed. I don't think it's possible, but if it is, why bother, the enter key is right there. If you are the only user and want to make it super easy, consider setting your system so it doesn't require a password, that way when you choose your operating system in grub, it just logs you in. I go passwordless (not recommended by most people), but I am the only user, and I'm in a private home where noone except my wife has access to my computer. As far as a separate move to mouse to "fake" an enter key press, more work IMHO, but to each his own. I am by no means an expert on these things, I'm still a noob to linux, but I think what your trying to do is a waste of time.

---

### Post by grahammechanical on 2021-05-29
I would like to add something. Fingerprint readers. No, I do not wish to add a fingerprint reader to my system. I want to make the point that a fingerprint is a username and not a password. We leave our fingerprints all over the place. Let us not fool ourselves into thinking that a fingerprint reader will make our system more secure. It will only make it easy to login.

Regards

---

### Post by vitalifrolov on 2021-05-29
The mouse button would be convenient when I use the touch screen.

---

### Post by TheFu on 2021-05-29
> **grahammechanical said:**
> I would like to add something. Fingerprint readers. No, I do not wish to add a fingerprint reader to my system. I want to make the point that a fingerprint is a username and not a password. We leave our fingerprints all over the place. Let us not fool ourselves into thinking that a fingerprint reader will make our system more secure. It will only make it easy to login.

Regards

Remember reading about a study of iPhone fingerprint cracking.  Researchers found that with 20 pre-created "fingerprints", they could unlock any iphone.  Over  time, we've each simplified the meaning of "fingerprint  equals 1 unique person in the world" and transferred that to a highly simplified variant used by a $20 computer visual comparison program which is more like "One of 20 fingerprints matches everyone in the world."

Vastly different from the original idea.

---

