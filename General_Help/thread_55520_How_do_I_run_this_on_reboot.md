---
title: "How do I run this on reboot?"
date: 2005-08-09
forum: General Help
---

### Post by macewan on 2005-08-09
```
sudo setpci -v -s : latency_timer=40
```

I need this to run automaticly if the system is rebooted

Currently I have to do this manually. ](*,)

---

### Post by strikeforce on 2005-08-09
I'm not sure if it works however try creating a file under your rcS.d/ directory and it'll get run every boot however take sudo out because startup is run as root anyways.

Obviously if I'm wrong tell me but thats my understanding.

I'll try and explain further.

Create a new file called bootupprogs
```

sudo gedit /etc/rcS.d/bootupprogs

```

Enter that line in there
```

#!/bin/sh
setpci -v -s : latency_timer=40

```

---

### Post by macewan on 2005-08-09
Thanks, it's been bugging me.



[QUOTE=strikeforce]I'm not sure if it works however try creating a file under your rcS.d/ directory and it'll get run every boot however take sudo out because startup is run as root anyways.

Obviously if I'm wrong tell me but thats my understanding.

I'll try and explain further.

Create a new file called bootupprogs
```

sudo gedit /etc/rcS.d/bootupprogs

```

Enter that line in there
```

#!/bin/sh
setpci -v -s : latency_timer=40

```[/QUOTE]

---

### Post by macewan on 2005-08-09
OK, this is how to do it:


 cd /etc/init.d/
sudo vi bootupprogs

```
#!/bin/sh
setpci -v -s : latency_timer=40
``` 

sudo chmod +755 bootupprogs
cd /etc/rcS.d
sudo ln -s ../init.d/bootupprogs S71bootupprogs

---

