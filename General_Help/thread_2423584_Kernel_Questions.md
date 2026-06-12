---
title: "Kernel Questions"
date: 2019-07-25
forum: General Help
---

### Post by john.f2017 on 2019-07-25
I recently upgraded from 18.10 to 19.04 and I had some problems in the final install ("Could not install shared mime info" and ",  "a recovery will now run (dpkg --config -a".) I seem to have resolved those but one thing I'm noticing is that my wifi/bluetooth has become hinky. I used to be able to go considerable distances (from my laptop) and still have good wifi and bluetooth connections and now it's become choppy and drops completely. I've investigated the matter and one of the things I'd like to try is going back to an earlier kernel. At boot I'm only offered two recent kernel options, both point 5. and both coming, as I recall, with 19. I've tried both.  

I have a couple of questions related to this. 

1) When I run the command: "dpkg --list | grep linux-image", besides the two point 5. kernels, I have listed at least six point 4. related kernels but these are no where to be found for selection at "advanced startup"; just the two point 5.s. 

2) I deliberately gave myself a big /boot so I could keep kernels but now it seems they get deleted with each update aside from two. How can I keep grub from deleting these old kernels upon update? 

3) Can I reinstall one of the point 4. related kernels so I can try it out and see if it gives me back a better wifi/bluetooth signal? 

4) If I want to delete these point 4. entries later on, how would I go about doing that? There's no actual kernel attached to the entry it seems;  just an entry that shows up under that command.

Thanks.

---

