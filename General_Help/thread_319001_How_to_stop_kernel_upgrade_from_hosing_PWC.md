---
title: "How to stop kernel upgrade from hosing PWC?"
date: 2006-12-14
forum: General Help
---

### Post by rafemonkey on 2006-12-14
When I first set up Ubuntu, I had to install the Saliard version of PWC to get my webcam to work. Recently, I've been trying to squeeze a little performence out of my via UnichromePro graphics array. And, in the the process I ran an `aptitude upgrade` which brought me the new kernel 2.6.17.1-10.34. Hooray... but after the update was done, my webcam was back to  an all grey image. a little poking around gave the following...

```

rclancy@sol:~$ lsmod |grep pwc
pwc                    51964  1 
compat_ioctl32          2432  1 pwc
videodev               10752  2 pwc
usbcore               134912  7 pwc,snd_usb_audio,snd_usb_lib,usbhid,ehci_hcd,uhci_hcd

``` 

The Kernel upgrade down-graded my copy of PWC... It's not hard to fix, but I'd rather not have this happen every time some incremental kernel patch comes out. How can I prevent this? Even better, is there some way to get the working Saliard version of PWC rolled into the main distro?

---

