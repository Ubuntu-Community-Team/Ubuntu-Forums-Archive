---
title: "Execute Script Before Shutdown Sequence (GUI Still Available)"
date: 2013-12-01
forum: General Help
---

### Post by maxwellcom on 2013-12-01
I made a simple script that issues a network signal to shut down a virtual machine running in vmplayer:

```

#!/bin/bash

#if vm is running, send shutdown signal and wait 5m for shutdown.

counter=1
credentials="/home/<user>/Credentials/.vmcred"
vm="<virtual machine name>"

while  
  ps cax | grep vmware-vmx > /dev/null 2>&1
do
  if [ $counter -eq 1 ]; then
    source "$credentials"
    net rpc shutdown -I "$vm" -U "$unpass"  #unpass defined in credentials file
  fi
  sleep 5
  if [ $counter -ge 60 ]; then
    echo "Virtual machine failed to shut down for some reason..."
    break
  fi
  echo "($counter) Virtual machine is shutting down..."
  counter=$[counter + 1]
done

exit 0

```

The script works great for routines like automated backups of the vm.  But I would like to execute this script as part of the shutdown sequence for Ubuntu 13.10.  I have tried adding this script to .bash_logout and rc0.d/rc6.d already with no success.  The problem is that the script needs to happen *before* the kill signal is sent to any process, and before the actual desktop session is closed.  In short, when a shutdown is requested, this script needs to run first and then continue a normal shutdown process.

Is this possible, and if so, then how?

---

### Post by erind on 2013-12-01
Maybe it's easier to incorporate a shutdown command right after your main script:

```
#!/bin/bash

#if vm is running, send shutdown signal and wait 5m for shutdown.

counter=1
credentials="/home/<user>/Credentials/.vmcred"
vm="<virtual machine name>"

while ps cax | grep vmware-vmx > /dev/null 2>&1
 do

 [...]

done

# exit 0

## *Final check and shutdown.*

**pgrep vmware-vmx || sudo shutdown -h now**
[I]
## or simply shutdown no checks.[/I]
# sudo shutdown -h now
```

That's how I shutdown (actually suspend) my VMs and then go for a full shutdown in my setup.

---

### Post by maxwellcom on 2013-12-02
> **erind said:**
> Maybe it's easier to incorporate a shutdown command right after your main script:

That would work if I could somehow modify the standard GUI shutdown to point to the main script.  At least then I could try to remember to always shutdown via GUI (and not "shutdown -h now" from CLI).  The implementation here is because I'll often shutdown the system and forget to bring down the virtual machine first.  I'm trying to work out an automated graceful halt sequence.

I'll see if I can figure that out...

---

### Post by erind on 2013-12-02
> **maxwellcom said:**
> [...]

The implementation here is because I'll often shutdown the system and forget to bring down the virtual machine first.  I'm trying to work out an automated graceful halt sequence.

[...]

I see, I've done that too. In my case I've created another custom shutdown icon (launcher) on the upper panel, that points to my special script that shuts down gracefully the VMs first then the whole system, and I rarely use the GUI shutdown. Never had any issues with my VMs since. Btw, I've also edited the sudoers file to include my script so I don't get prompted for password when shutting down.
Not too complicated and it works for me, your mileage may vary.

---

### Post by maxwellcom on 2013-12-03
> **erind said:**
> I've also edited the sudoers file to include my script so I don't get prompted for password when shutting down.

Using [this post]("http://askubuntu.com/questions/155791/how-do-i-sudo-a-command-in-a-script-without-being-asked-for-a-password") I modified the script to allow a sudo shutdown and implemented a launcher - seems like it will do the trick.  Thanks!

```

#if vm is running, send shutdown signal and wait 5m for shutdown.

counter=1
credentials="/home/<user>/Credentials/.vmcred"
vm="<virtual machine name>"

while  
  ps cax | grep vmware-vmx > /dev/null 2>&1
do
  if [ $counter -eq 1 ]; then
    source "$credentials"
    net rpc shutdown -I "$vm" -U "$unpass"  #unpass defined in credentials file
  fi
  sleep 5
  if [ $counter -ge 60 ]; then
    echo "Virtual machine failed to shut down for some reason..."
    break
  fi
  echo "($counter) Virtual machine is shutting down..."
  counter=$[counter + 1]
done

#if vm is shutdown, issue system halt
pgrep vmware-vmx || sudo /home/<user>/Script/syshalt.sh

```

---

### Post by Lars Noodén on 2013-12-03
The 'ps cax | grep' clause could probably be replaced by a simple 'pgrep -x'

As far as launching the script, have you considered an [upstart script](http://upstart.ubuntu.com/cookbook/)?  Those can be set to be triggered in the event of a [reboot or shutdown](http://upstart.ubuntu.com/cookbook/#how-to-establish-a-jobs-start-on-and-stop-on-conditions).  Even a sequence relative to the other scripts can be specified, that it won't execute until another or others have finished.

---

### Post by maxwellcom on 2013-12-11
> **Lars Noodén said:**
> have you considered an [upstart script](http://upstart.ubuntu.com/cookbook/)?

While originally researching a solution, I did come across that very link.  It looks like a robust replacement for init.d and likely to allow the sort of controlled vm shutdown I'm trying to develop, but I wasn't clear on a couple things.

First, Init.d (which I tried first) failed because while it executes shutdown scripts in sequence, I couldn't prevent the desktop session from being terminated first.  Will upstart allow a shutdown script to run before any other changes to the system's state are initiated?

Second, the vm shutdown process can take 20s or 5m; will upstart hold the shutdown process until the script has terminated, or will it start killing processes after a period of time?

The solution erind provided above works great, so long as I initiate a manual shutdown.  In other scenarios, such as remotely shutting down the host or a low-battery shutdown (it's a laptop), the vm is killed.

---

### Post by Lars Noodén on 2013-12-11
It might be a matter of choosing to act on a [different state](http://upstart.ubuntu.com/cookbook/#job-states) for the other service, such as "stopping"   I've only dabbled a little with upstart myself.  

Maybe "stop on stopping desktop-shutdown" (or "stop on starting desktop-shutdown" I'm not sure) or whatever lightdm.conf emits itself on shutdown.

---

### Post by ian-weisser on 2013-12-11
/etc/init/lightdm.conf emits desktop-shutdown.
Perhaps a pre-stop stanza there?

---

### Post by maxwellcom on 2013-12-12
> **ian-weisser said:**
> /etc/init/lightdm.conf emits desktop-shutdown.
Perhaps a pre-stop stanza there?

I am very happy to report success.

**First,** I created the script /home/<user>/Script/vmhalt:

```
#!/bin/bash

# set primary variables
credentials="/path/to/credentials/file/.vmcred"

if pgrep -x vmware-vmx > /dev/null 2>&1; then

  # send vm shutdown signal with user credentials
  source "$credentials"
  net rpc shutdown -I "<vm>" -U "$unpass"  #unpass defined in credentials file

  # wait 5m for vm shutdown.
  counter=1
  while pgrep -x vmware-vmx > /dev/null 2>&1; do
    sleep 5
    if [ $counter -ge 60 ]; then
      break
    fi
    counter=$[counter + 1]
  done

fi

exit 0
```

**Next,** I edited /etc/init/lightdm.conf. Directly underneath the line "emits desktop-shutdown" I added:

```
pre-stop script
    exec sudo -u <user> /home/<user>/Script/vmhalt
end script
```

The result is that any shutdown (graphical, shell or remote) will hold the desktop open, wait for the virtual machine to shutdown gracefully, and then continue with a normal shutdown.

---

### Post by maxwellcom on 2013-12-14
**Update: ** Because of Ubuntu's curious hybrid state between upstart and init.d/SysV (I think), I had to add one additional step so that the graceful shutdown would work in every scenario.

To init.d I added a similar process-checking loop:

```
#!/bin/bash
if pgrep -x vmware-vmx > /dev/null 2>&1; then
  counter=1
  while pgrep -x vmware-vmx > /dev/null 2>&1; do
    sleep 1
    if [ $counter -ge 600 ]; then
      break
    fi
    counter=$[counter + 1]
  done
fi
exit 0
```

I then linked this script in rc0.d and rc6.d, inserted just before the "sendsigs" script in each.  The result is basically a second "hold up" on the vmware-vmx process to prevent any kill signal being sent to any process by the old SysV.  I suspect that when all Ubuntu packages are updated and Canonical has booth feet in upstart, this addition will become obsolete.

---

