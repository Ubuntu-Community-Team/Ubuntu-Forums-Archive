---
title: "Youtube sound not working after Jack install"
date: 2014-07-27
forum: General Help
---

### Post by bencouve on 2014-07-27
Hello guru's

Please help if you can. I am trying to get Ardour to run on ubuntu 14.04. Have installed Jack and Ardour which appear to be working. However, Jack is taking control of the sound card so cannot play sound from youtube etc...

I have done some research but have come up trumps at the moment. Did follow instructions for a kind of related issue and have the URL output for someone to check if it helps. Followed the instructions from here
[https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)
and the output is located here
[http://www.alsa-project.org/db/?f=03a9905163ee4c323d8c79a951f67a4675c69db7](http://www.alsa-project.org/db/?f=03a9905163ee4c323d8c79a951f67a4675c69db7)

This may not be useful but may save time if it is. Thanks in advance for any info that can be provided.

---

### Post by Bucky Ball on 2014-07-27
Might sound dumb, but what happens when you switch off Jack? On my system, it reverts to Alsa/Pulse.

---

### Post by bencouve on 2014-07-27
Hi Bucky-ball. Thanks for the input. It was quite a logical one really. I tried stopping Jack from the interface but youtube still did not work so I killed the process. When I tried to start jack again I get " 
D-BUS: JACK server could not be started.

 

 Sorry

Which is fine for the time being.

Thanks for the help

---

