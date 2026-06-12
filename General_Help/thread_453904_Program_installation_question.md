---
title: "Program installation question"
date: 2007-05-24
forum: General Help
---

### Post by dryder on 2007-05-24
Hi,
Edgy & Feisty

I have efax and efax-gtk installed.

I want to try hylafax to see if it is more versatile.

If I install hylafax can I leave efax in so I have a working fax while I work out, what I understand to be, the rather complicated setup of hylafax?

Obviously I would not run both at the same time but does it matter if they exist and I choose which I want to use 'on the day'?

Many thanks.

David

---

### Post by mbradlcu on 2007-05-25
I'm not sure how hylafax can be invoked but I would guess it's either run at startup with a init.d script, or run explicitly with an option to run as a daemon like ntop does.. Anyway you should be able to have both on your system and just run one at a time.. and shutting down either one would be just a matter of 'ps -aef |grep {efax hylafax}' and killing the process,, or killalll {efax hylafax},,, our '/etc/init.d/hylafax stop | start' . Let me know if you have any questions about these methods.

---

### Post by dryder on 2007-05-26
Hi mbradlcu, my apologies for the late reply.

I understand from your post that I can install both and choose which one to invoke.

The method, I am afraid, loses me ... no offence intended :-)
David

---

### Post by mbradlcu on 2007-05-27
no offense taken!,
I'm guessing (and please let me know if it's otherwise) you have an icon to click in your menu lists.
If these programs run in the background,, or for that matter are automatically started you can end the programs using the 'kill' command in a shell/terminial
```
ps -aef | grep hylafax
```
if it's running you'll see a process number, you can end the process like this:
```
kill -15 12345
```
were "12345" is the number that was displayed by the 'ps' command.
The same holds for efax. 
Play around with it and if you have any questions let me know.
have fun!

---

