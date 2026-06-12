---
title: "scripting problem"
date: 2008-02-06
forum: General Help
---

### Post by ectraz on 2008-02-06
hi, haveing some problems script.
for some reason flagging up an error im pretty sure its a security issue but unsure how to resolve it thanks in advanced

The error:::
/cameras/script/m4mdovercamera1_script: line 4: usermod: command not found


The script im useing:::
#!/bin/bash
mkdir /cameras/mad4mobiles/dover/camera1/dover`date +%d%m%y`
chmod 777 /cameras/mad4mobiles/dover/camera1/dover`date +%d%m%y`
usermod -d /cameras/mad4mobiles/dover/camera1/dover`date +%d%m%y` m4mdovercamera1


The crontab im useing to execute the script:::
50 * * * * sh /cameras/script/m4mdovercamera1_script

Clint

---

### Post by geirha on 2008-02-06
> **ectraz said:**
> hi, haveing some problems script.
for some reason flagging up an error im pretty sure its a security issue but unsure how to resolve it thanks in advanced

The error:::
/cameras/script/m4mdovercamera1_script: line 4: usermod: command not found


The script im useing:::
#!/bin/bash
mkdir /cameras/mad4mobiles/dover/camera1/dover`date +%d%m%y`
chmod 777 /cameras/mad4mobiles/dover/camera1/dover`date +%d%m%y`
usermod -d /cameras/mad4mobiles/dover/camera1/dover`date +%d%m%y` m4mdovercamera1


seems /usr/sbin is not in $PATH when the script is run. you could change the last line to ```
/usr/sbin/usermod -d /cameras/mad4mobiles/dover/camera1/dover`date +%d%m%y` m4mdovercamera1
```

> **ectraz said:**
> 
The crontab im useing to execute the script:::
50 * * * * sh /cameras/script/m4mdovercamera1_script

Clint
The first line of the script, "#!/bin/bash", says that this script should be run with bash, but you run it with sh. It'll probably work, but it's better to be consistent.
```
50 * * * * /bin/bash /cameras/script/m4mdovercamera1_script
```

---

