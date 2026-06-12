---
title: "how close 2d package manager, use run with superuser privilidges"
date: 2007-05-16
forum: General Help
---

### Post by smartsteps on 2007-05-16
My computer locked up while loading virtual box from a cd. 

I rebooted and tried to load the same program from the internet and received a error message that only one software management tool  is allowed to run at the same time.  I tried rebooting twice and it did not help. 

I found synaptic package manager and it reports; " the error dpkg was interrupted, you must manually run 'dpkg --configure -a' "  

I went to terminal and typed this command and it says I have to have superuser privilidges to use this program. 

I am a newby, just loaded Ubundu yesterday.    

Can anyone tell me what I need to do to close the second package manager and to run the error correction and how to get superuser privileges?  Thanks

---

### Post by kaamos on 2007-05-16
sudo stands for super user do, so just prefix the command with that:
```
sudo dpkg --configure -a
```

---

