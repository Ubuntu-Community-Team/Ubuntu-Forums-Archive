---
title: "How can I record online radio stream?"
date: 2005-06-22
forum: General Help
---

### Post by washman on 2005-06-22
I want to record some bbc online radio programs, streamripper doesnt work(because the programs are real audios stream?).  which software should I choose?

thanks in advance. :)

---

### Post by didit on 2005-06-22
you can use streamtuner

---

### Post by washman on 2005-06-22
many thanks,

How can I use it to rip real audio stream (ram)? just input the location?

---

### Post by xalphas on 2005-06-22
Follow here and you will have success  :) 
[http://ubuntuforums.org/showthread.php?t=28356](http://ubuntuforums.org/showthread.php?t=28356)

---

### Post by washman on 2005-06-23
Thank you, but streamtuner still needs streamripper, which is not able to record ram stream ](*,) 

Do I have to install a mplayer? but I have got totem....... :roll:

---

### Post by k4p0w3r on 2005-06-23
I listen alot to swedish radio because every friday at 8pm they have live broadcast with various artists. SR (swedish radio) only broadcast in Real audio.
Here's how I solved it:

How to record a live-stream from Realplay or similar program.

Simple explanation:
Vsound can capture sound from any application that uses OSS /dev/dsp sound device. It basicly acts as a virtual cable between your computers "sound out" and redirects it to "line in". The sound can be saved to a wav file (using sox - automaticly).
More info can be found here:  [http://flatline.org.uk/vsound/](http://flatline.org.uk/vsound/)


1.	Install vsound
1.1	command for debian based systems: apt-get install vsound
1.2	note: vsound may require sox

2. 	Run vsound with these arguments:
2.1	command: vsound -f myrecording.wav -d soundapplication soundstream
2.2	example: vsound -f p3hiphoplive.wav -d /opt/RealPlayer/realplay rtsp://sr-rm.qbrick.com/broadcast/cluster/encoder/02038_p3.rm
2.3	note: -f outputs to the file mentioned. -d make sure you can listen to the sound at the same time it is recorded. Some applications like RealPlayer need this to work.

After the recording is made (file will be written after you close the Realplayer) just convert the wav to ogg or mp3  \\:D/

---

### Post by artinla on 2005-06-23
I vote we pin this in the howtos


Art

---

### Post by blitze on 2005-06-30
[QUOTE=artinla]I vote we pin this in the howtos


Art[/QUOTE]

I Second this

---

### Post by Talldave2002 on 2005-08-21
[QUOTE=k4p0w3r]I listen alot to swedish radio because every friday at 8pm they have live broadcast with various artists. SR (swedish radio) only broadcast in Real audio.
Here's how I solved it:

How to record a live-stream from Realplay or similar program.

Simple explanation:
Vsound can capture sound from any application that uses OSS /dev/dsp sound device. It basicly acts as a virtual cable between your computers "sound out" and redirects it to "line in". The sound can be saved to a wav file (using sox - automaticly).
More info can be found here:  [http://flatline.org.uk/vsound/](http://flatline.org.uk/vsound/)


1. Install vsound
1.1 command for debian based systems: apt-get install vsound
1.2 note: vsound may require sox

2.  Run vsound with these arguments:
2.1 command: vsound -f myrecording.wav -d soundapplication soundstream
2.2 example: vsound -f p3hiphoplive.wav -d /opt/RealPlayer/realplay rtsp://sr-rm.qbrick.com/broadcast/cluster/encoder/02038_p3.rm
2.3 note: -f outputs to the file mentioned. -d make sure you can listen to the sound at the same time it is recorded. Some applications like RealPlayer need this to work.

After the recording is made (file will be written after you close the Realplayer) just convert the wav to ogg or mp3  \\:D/[/QUOTE]


I found that this works, but dosent work for BBC files.

I found a work around though.

Use the BBC Radio Player as usual, once the stream is playing right click on the Play in Stand alone player link, and save the link address. (this will be the RAM link not the HTML)

Then use the Vsound as posted above. 

Hope this works for you.

---

### Post by tonderai on 2005-12-03
You can use Vsound with Firefox itself to record bbc radio shows that don't have an 'open in standalone player' link (which seems to be most). Just use the html link for the show in the radio player as the 'soundstream' (post #6) and firefox as the 'soundapplication'.

Of course I would only advocate using this for personal use - just like taping shows from fm.

---

### Post by 3zrael on 2006-02-28
Thank you very much for this thread, I spent one hour trying to understand why streamripper wasn't working with rm streaming... ](*,)

---

