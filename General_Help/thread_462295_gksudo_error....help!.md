---
title: "gksudo error....help?!"
date: 2007-06-02
forum: General Help
---

### Post by nebhead on 2007-06-02
i am making this post in despair, as i can't do anything because of the problem i am facing.
whenever i run synaptic or any other program that prompts me for a password it freezes and i am unable to do anything other than hard power-off.
what happens is the screen darkens..as it does, the password box appears, i type in my password, and instead of synaptic starting up the screen stays dark and is frozen. nothing happens, even after quarter of an hour, still frozen.  so i can't install anything through synaptic or any thing else that requires a password box....i am really stuck on this, help please?!

---

### Post by aysiu on 2007-06-02
Open up a [terminal](http://www.psychocats.net/ubuntu/terminal) and paste this command in: ```
gksudo synaptic
``` When it freezes, see what (if any) error appears. Then post the error back here.

---

### Post by loathsome on 2007-06-02
Did you do anything to your /etc/network/interfaces file?

Does this happen if you try using «kdesu» as well?

---

### Post by nebhead on 2007-06-03
i feel so stupid, i forgot to mention i was running beryl, that was the problem. 
the thing that was causing it "undirect fullscreen windows"
thanks for your time anyway :D

---

### Post by loathsome on 2007-06-03
> **nebhead said:**
> i feel so stupid, i forgot to mention i was running beryl, that was the problem. 
the thing that was causing it "undirect fullscreen windows"
thanks for your time anyway :D
Glad to hear that you solved out your issue! ;)

---

### Post by Freaky_Llama on 2007-06-06
I used google to locate this thread.

I just wanted to note that this fix worked for me as well. It also fixed a problem I was having with Gnome starting up. Before it would take 20 seconds for the splash screen to appear after logging in. Now, its about 5 until the splash screen starts.

---

