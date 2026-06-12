---
title: "Sound from a doc file"
date: 2006-08-18
forum: General Help
---

### Post by JimS on 2006-08-18
...
I received a doc file with a speaker icon.  I am asked to double
click on the speaker icon and I will hear the sound.  When I click on
the speaker icon, instead of sound I get another document with
code.  The first 2 lines of code looks like this:
RIFF#x##WAVEfmt #########+###+######fact####&#65533;w##data&#65533;w##}}}}&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;

I have successfully gotten sound on my WinXP box using
Star Office writer to view the doc and
then double clicking on the speaker icon.
I don't know what program generates the sound.

What do I need to do to get sound on both my Breezy box
and Dapper notebook.

If you want me to send you the doc file, I will.  It is
very funny.

I sent it to YOUSENDIT.
see
[http://www.yousendit.com/transfer.php?action=download&ufid=AACD42E666BAF640](http://www.yousendit.com/transfer.php?action=download&ufid=AACD42E666BAF640)
...

---

### Post by JimS on 2006-08-19
...
I see that no one has replied.

It is difficult to believe that no one has had a sound file imbedded in a doc file.

Please download the file and check it out.

Like I wrote in my first message, it works in MS Windoz.  Why not in Ubuntu?
...

---

### Post by qamelian on 2006-08-19
> **JimS said:**
> ...
I see that no one has replied.

It is difficult to believe that no one has had a sound file imbedded in a doc file.

Please download the file and check it out.

Like I wrote in my first message, it works in MS Windoz.  Why not in Ubuntu?
...
Sound files are embedded in MS Word and other office documents using Activex controls. Activex does not exist on Linux.

---

### Post by JimS on 2006-08-19
...
gamelian,
Thanks for the answer.
How can I check if in my case the sound is in fact Activex created?
Is anyone working on the lack of Activex in Linux?
I see a bit when I google 'activex linux'.
But it doesn't look promising.
Thanks again.

Anyone else?
...

---

### Post by qamelian on 2006-08-20
> **JimS said:**
> ...
gamelian,
Thanks for the answer.
How can I check if in my case the sound is in fact Activex created?
Is anyone working on the lack of Activex in Linux?
I see a bit when I google 'activex linux'.
But it doesn't look promising.
Thanks again.

Anyone else?
...
Highly unlikely. Most folks consider lack of Activex to be a good thing as it is insecure by design. 
If the sound is embedded in in a Word document, it has to be by means of an Activex control. The only other alternative to play a sound from a document would be to link to an external file, in which case you would need to have the separate sound file as well.

---

