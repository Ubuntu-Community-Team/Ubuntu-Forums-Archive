---
title: "Stopping BOINC"
date: 2007-11-05
forum: General Help
---

### Post by dryder on 2007-11-05
Hi
Feisty 

Does anybody know how I stop BOINC tasks running?

I need to stop them for a while and File>Exit in BOINC Manager only stops the GUI not the tasks.

I want to avoid ungracefully killing the processes in case that results in data not being written to file causing a corruption,

Many thanks,

David

---

### Post by dcstar on 2007-11-05
> **dryder said:**
> Hi
Feisty 

Does anybody know how I stop BOINC tasks running?

I need to stop them for a while and File>Exit in BOINC Manager only stops the GUI not the tasks.

I want to avoid ungracefully killing the processes in case that results in data not being written to file causing a corruption,

Many thanks,

David

Activity-Suspend.

---

### Post by dryder on 2007-11-05
Thanks - I wasn't sure if that would be the same as stopping the service (net stop boinc) in Windows.

Thank you very much for clearing that up. :-)

David
(Have you got a laptop with you at the Melbourne Cup?  ...)   :-)

BTW - I did search the forums ... I agree with your signature

---

### Post by ShirishAg75 on 2007-11-10
There is also 

sudo /etc/init.d/boinc-client stop which also works. That is for stopping the boinc-client daemon

---

### Post by dryder on 2007-11-10
Thanks - that was the one I was after - I had previously killed the process to stop it.

Cheers,
David

---

### Post by Skip Da Shu on 2007-11-12
OR even easier... from the GUI BOINC Manager top menu ADVANCED>Shut Down Connected Client will stop the service/daemon on the machine the GUI is connected to... Windows or Linux.

Skip

---

### Post by dryder on 2007-11-12
> the GUI BOINC Manager top menu ADVANCED>Shut Down Connected Client is not in my 5.4.11 version of Boinc Manager>Advanced menu  ...

---

### Post by Skip Da Shu on 2007-12-04
> **dryder said:**
> Hi Delete Me!

---

### Post by Skip Da Shu on 2008-02-24
> **dryder said:**
> is not in my 5.4.11 version of Boinc Manager>Advanced menu  ...

You can use synaptic or apt-get to upgrade to v5.10.8

From there you can actually overlay the executables (boinc_client, boinc_cmd and boincmgr) with the v5.10.28s from the download on the Berkeley site.... if ya wanna.

---

### Post by Skip Da Shu on 2008-02-25
**Don't use the BOINC_OPTS="--daemon" parameter in your /etc/default/boinc-client file**

.......................................

**Original Problem:** Below didn't stop the daemon client```
sudo /etc/init.d/boinc-client stop
```
**Related:** Below didn't function properly ```
sudo /etc/init.d/boinc-client [restart or status]
``` 
**Cause:** Usage of the BOINC_OPTS= "--daemon" parameter in the file /etc/default/boinc-client
**Detail:** For reasons not directly known to me the boinc_client option "--daemon" caused the file /var/run/boinc_client.pid to contain a value lower (by 1 or more) than the what is displayed as the current pid for the boinc_client via "ps -U boinc -u boinc" or "ps -C boinc_client".  This causes the function "is_running()" to obtain an incorrect pid number from the .pid file.  In the function stop() the start-stop-daemon appears to fail due to the incorrect pid number in the file but no check of it's success or failure is done so the script reports "OK" to the stop command without having actually terminated the process.  The function status() always reports the client is stopped.

With boinc_client running entering "sudo /etc/init.d/boinc-client x where x is:

[LIST=1]
[*]status - returns " * Status of BOINC core client: stopped." - it is not.

[*]stop - returns: " * Stopping BOINC core client: boinc_client                                                            [ OK ]" - it does not.

[*]start returns: "* Starting BOINC core client: boinc_client                                                            [ OK ]" - it is already running and should throw an error.
[/LIST]

With boinc_client NOT running entering "sudo /etc/init.d/boinc-client x where x is:

[LIST=1]
[*]status - returns " * Status of BOINC core client: stopped." - it is.

[*]stop - returns: " * Stopping BOINC core client: boinc_client                                                            [ OK ]" - it is not running and should throw an error.

[*]start - returns: "* Starting BOINC core client: boinc_client                                                            [ OK ]" - it starts the boinc daemon

[*]restart - returns: both the above stopping and starting messages.
[/LIST]

It appears that the "--daemon" parameter is no longer required or desired.  I have not yet identified any loss of functionality by omitting this.

---

