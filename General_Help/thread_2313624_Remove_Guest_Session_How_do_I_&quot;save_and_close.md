---
title: "Remove Guest Session: How do I &quot;save and close&quot;?"
date: 2016-02-14
forum: General Help
---

### Post by sks24 on 2016-02-14
I'm trying to follow the directions [here]("http://askubuntu.com/questions/451526/removing-guest-session-at-login-in-ubuntu-14-04") to remove the guest session in an Ubuntu 14.04 installation. After adding the "allow-guest=false" line, I can't figure out how to save and close. What are the exact keys I hit to do that? 

I tried the second method listed, and it rendered rendered the system unbootable.

---

### Post by steeldriver on 2016-02-14
If you're using the nano editor, that would be Ctrl-O and Ctrl-X

---

### Post by sks24 on 2016-02-14
Ctrl shift o and Ctrl shift x 
and Ctrl-o and Ctrl-x 

Either one gives me a pop-up when I try to exit the terminal: "Close this terminal? There is still a process running, etc."

I tried both of those earlier, btw. This is baffling.

---

### Post by sks24 on 2016-02-14
And yes, this appears to be the nano editor: "GNU nano..."

---

### Post by sks24 on 2016-02-14
Am I missing something with the commands and case? Because hitting the Ctrl key and the O key is really Ctrl-o, no? In any event, "Ctrl" then "O", and then "Ctrl" then "X" either in sequence, or both at the same time then releasing both, doesn't appear to do anything at all. I'll reboot, and the guest session is still there.

---

### Post by oldos2er on 2016-02-14
In nano, Ctrl-o saves and Ctrl-x exits. No "shift" in there.

---

### Post by sks24 on 2016-02-14
I'm not sure why or how the Crtl o worked this time, but now I can't get past this: 
[IMG]https://drive.google.com/file/d/1mHkT0mEOk-D5Qb3acv5wMT5Gls0JYFo3Uw/view?usp=sharing[/IMG]

---

### Post by sks24 on 2016-02-14
If I select "No", it won't exit.

---

### Post by sks24 on 2016-02-14
If I select "N", then it takes me back to this prompt: [https://drive.google.com/file/d/1BtWxTBRetyectBHF7mPpt61pweK4eMVnCg/view?usp=sharing]("https://drive.google.com/file/d/1BtWxTBRetyectBHF7mPpt61pweK4eMVnCg/view?usp=sharing")

---

### Post by steeldriver on 2016-02-14
so if you are trying to re-save it as 50-ubuntu.conf just backspace over the 'o' and 'x' and then press 'Enter'?

---

### Post by sks24 on 2016-02-14
Well, something worked. Maybe that's what I did. IDK: I kept pawing at it and something happened and now the guest account is no longer present on log-in. 

Thanks for your help! :)

---

### Post by ajgreeny on 2016-02-14
I am a bit confused about what you are doing but Ctrl=o will offer to save the file with the same name as when you opened it, but you have to use Enter to accept that, then Ctrl+x will close nano and take you back to the terminal prompt.

---

### Post by sks24 on 2016-02-14
What I missed here is pressing the enter key after Ctrl - o.

---

