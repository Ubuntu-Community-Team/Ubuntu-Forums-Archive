---
title: "Software Updater drops screen to low-res after reboot every time: Ubuntu 18.04 with N"
date: 2020-05-17
forum: General Help
---

### Post by troyshelby on 2020-05-17
I posted this on another forum and didn't get any replies. Hopefully someone here knows the answer.

                      For the last few years, every time the Software Updater installs  updates and I allow it to reboot the system, the system comes back up in  low resolution. 
  I have a manual workaround which I describe below, which I hoped was  only temporary - until a patch magically solved the problem. But this  has been getting annoying enough to try and do something about it.
  The system comes back up in low resolution mode (looks like 640x480  or 800x600). When I go into Software & Updates -> Additional  Drivers, the nvidia-driver-440 (proprietary, tested) is selected in the radio button group.


  [IMG]https://i.stack.imgur.com/FMabN.jpg[/IMG]

  
My workaround is clicking on the Nouveau radio button, clicking  apply, then clicking back on the NVidia driver button, clicking apply  again (this takes about a minute), rebooting. And then everything is  back to normal.

  I was wondering if there was a way of avoiding having to do this  every time there is an update? I did a search for this but could not  find anything definitive. I would have thought that quite a few people  would be having this problem?

---

