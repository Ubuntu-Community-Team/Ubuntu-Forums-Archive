---
title: "Skype and Microphone problem"
date: 2006-10-23
forum: General Help
---

### Post by highllamas on 2006-10-23
Hi guys.
I have a strange problem using Skype. When I talk with a friend (who uses xp)  sometimes the microphone volume goes down to half or more (I see it from the volume control). The problem is that I have to raise it every time otherwise I can't be heard loud enough on my friend's PC. I think that this happens when my friend speaks a little bit loud (not shout just a little louder:) ). Do you have any ideas why this is happening? I use a Sound Blaster Audigy PCI card.
Thanks.

---

### Post by highllamas on 2006-10-24
I think I found the solution for the problem above. At least it worked for me...
I write it down in case someone else has the same one too.

Before doing this be sure that Skype is NOT running. Otherwise your PC might freeze as mine did...

Open the file ~/.Skype/shared.xml (with a text viewer for example)

Find the tags <VoiceEng>...</VoiceEng> 20-30 lines before the end of file.

Add these in between them:

<AEC>0</AEC>
<AGC>0</AGC> 

Change the value to 255 between thse tags: <MicVolume>...</MicVolume>.

My file looked like this after these changes:
.......
    <VoiceEng>
      <AEC>0</AEC>
      <AGC>0</AGC>
      <AudioLib>1</AudioLib>
      <MicVolume>255</MicVolume>
    </VoiceEng>
........................ 

Save the file and start Skype for testing it.

I found this solution after some googling in the Skype forums. Here is the thread:
[http://forum.skype.com/index.php?showtopic=57685](http://forum.skype.com/index.php?showtopic=57685)

---

