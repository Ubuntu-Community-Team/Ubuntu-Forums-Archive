---
title: "Unresposiveness when apache asks for a pass phrase"
date: 2008-01-03
forum: General Help
---

### Post by marshall.robert on 2008-01-03
When booting up my newly created server it asks for a passphrase, not even sure what it is, but i can enter it because the terminal wont take in my keystrokes (apart from ctrl+alt+del), i have to log in and start an x session before it starts ispconfig else i cant do anythng...

can anyone please help?

---

### Post by cdenley on 2008-01-03
So apache asks for a password because you set up an SSL certificate, and you think you can't enter the password because it doesn't print a * for each character? For anything on the command line, when you enter passwords, no characters such as * are shown. You just have to type your password (even if you can't see what you're typing), then press enter.

---

### Post by marshall.robert on 2008-01-03
i know i cant enter a password cos not even the enter key responds, nor does any other key, plus it doesnt hide password characters, because i have seen multiple characters appear when ive got fed up and held down a key... so the error is not on my part.

---

### Post by cdenley on 2008-01-03
So the terminal won't let you enter keystrokes except ctrl+alt+del, and you're stuck at apache prompting for a password, but you managed to log in? Did you ctrl+c the apache script or switch to a virtual terminal so you can log in? If the apache script won't accept an enter keystroke, but the login will, then I have no idea what your problem is. Maybe you should post the exact output on the screen.

Also, I'm pretty sure it does hide the password characters if we're talking about the same script, but I'm not about to restart my web server to verify. If you get characters to print on the screen, then you probably either got the script to exit, or forked it into the background.

---

### Post by marshall.robert on 2008-01-03
i think labelled the title wrong, its something to do with ispconfig, i would change the title if i knew a way.

and i think its something to do with an rsa certificate, mentioning something to do with apache. it asks for a passphrase and i cant get any further because of the intermitance of the input. this is the first time ive done anything with a server, so im a bit nood here...

i tried ctrl+c, but with the intermitance of the input it didnt get through..

edit: never mind, i just redid everything, except ispconfig, and its fine now, thanks all the same :)

---

