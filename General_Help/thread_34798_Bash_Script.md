---
title: "Bash Script"
date: 2005-05-16
forum: General Help
---

### Post by computerguy867 on 2005-05-16
How would one go about writing a script that starts a demon, runs a program, and when the user terminates the program the demon will stop.  I want the HPOJ demon to start when xsane is opened and then stop when it is closed because it interfears with the Hp printing driver.  Thanks.

---

### Post by blueplazma on 2005-05-16
There's a ton of shell scripting tutorials online, and Ubuntu works fine with all of them.  Just make sure that the first line of all your scripts of 
```

#!/bin/sh

```
If you have a specific error, I'd be happy to help you but I'm not familiar with either of those programs, so you will need to get the script going on your own.

---

### Post by ssam on 2005-05-16
```
#!/bin/sh
xeyes &
xclock
killall xeyes
```

does roughly what you want.

for demons it might look more like

```
#!/bin/sh
/path/to/demon start
xclock
/path/to/demon stop
```

the & on the end of the line backgrounds a task. most demons should background them selves when started.

---

### Post by computerguy867 on 2005-05-16
Thanks alot!. i got it working.

---

