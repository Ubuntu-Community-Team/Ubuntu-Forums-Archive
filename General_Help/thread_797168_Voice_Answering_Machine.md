---
title: "Voice Answering Machine"
date: 2008-05-17
forum: General Help
---

### Post by rykel on 2008-05-17
Hi,

Is it possible to find a program for Ubuntu that basically acts as an "answering" machine?

That is, a program that:
[INDENT][LIST=1]
[*]Calls a number.
[*]Says, "Hi John, This is Rykel's robot. He wants to know if you are attending his dinner tonight. Press 1 if you are coming. Press 2 to decline."
[*]Waits for keypad response.
[/LIST][/INDENT]

If 1, program says, "Great. See you." If 2, it says, "Thank you."

---

### Post by h4mx0r on 2008-05-17
Festival program can communicate text to speech and based upon numerical input received from the modem you could have it send different speech over the connection. You could write simple bash scripts or perl programs to handle output/input and schedule them to be ran with cron. I'm still trying to figure out how it would all work exactly. I had the idea of doing the same before :)

After installing festival do echo "put message here" | festival --tts and it should speak. You'll also need to install an accent package.

---

### Post by rykel on 2008-05-17
Wow, thanks for that tip... keep this thread alive!

Let's see what others have to say about this automated answering system that runs from Ubuntu.

---

### Post by h4mx0r on 2008-05-17
Oh hey look into something called "Asterisks" it deals with doing a lot of weird stuff with phone lines. I read about it in a linux multimedia book I'll try to brush up on my understanding of it later.

---

### Post by h4mx0r on 2008-05-17
I think this can be done with festival or perhaps some other application. If you get a message on the answering machine how about it converts the audio to text and messages your cellphone using libpurple library from finch/pidgin. Speaking of cellphones you ever tried cuts? [http://www.codewar.net/cuts/](http://www.codewar.net/cuts/) access your system from your cellphone :)

---

### Post by rykel on 2008-05-17
Hey,

Something that is in a way related to this thread...

Take a look at this site - Pre-Recorded Audio Sound Files!
[http://evolution.voxeo.com/library/audio/prompts/home.jsp](http://evolution.voxeo.com/library/audio/prompts/home.jsp)

---

### Post by h4mx0r on 2008-05-17
Yeah useful if you like that old granny voice. I prefer the british female voice to festival, really hot :)

---

