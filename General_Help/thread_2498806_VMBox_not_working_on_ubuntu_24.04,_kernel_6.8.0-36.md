---
title: "VMBox not working on ubuntu 24.04, kernel 6.8.0-36 generic"
date: 2024-06-28
forum: General Help
---

### Post by khunguy on 2024-06-28
sudo apt install virtualbox-qt
...

vboxnetflt.ko.zst:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/6.8.0-36-generic/updates/dkms/
depmod...
[COLOR=#ff0000]Job for virtualbox.service failed because the control process exited with error code.
See "systemctl status virtualbox.service" and "journalctl -xeu virtualbox.service" for deta
ils.[/COLOR]
invoke-rc.d: initscript virtualbox, action "restart" failed.
× virtualbox.service - LSB: VirtualBox Linux kernel module
     Loaded: loaded (/etc/init.d/virtualbox; generated)
     Active: failed (Result: exit-code) since Thu 2024-06-27 21:10:58 PDT; 9ms ago
       Docs: man:systemd-sysv-generator(8)
    Process: 15347 ExecStart=/etc/init.d/virtualbox start [COLOR=#ff0000](code=exited, status=1/FAILURE)[/COLOR]
        CPU: 53ms

Jun 27 21:10:58 ryanowns-ZenBook-UX333FA-UX333FA systemd[1]: Starting virtualbox.service - 
LSB: VirtualBox Linux kernel module...
Jun 27 21:10:58 ryanowns-ZenBook-UX333FA-UX333FA virtualbox[15347]:  * Loading VirtualBox k
ernel modules...
Jun 27 21:10:58 ryanowns-ZenBook-UX333FA-UX333FA virtualbox[15347]:  * modprobe vboxdrv fai
led. Please use 'dmesg' to find out why
Jun 27 21:10:58 ryanowns-ZenBook-UX333FA-UX333FA virtualbox[15347]:    ...fail!
Jun 27 21:10:58 ryanowns-ZenBook-UX333FA-UX333FA systemd[1]: virtualbox.service: Control pr
ocess exited, code=exited, status=1/FAILURE
Jun 27 21:10:58 ryanowns-ZenBook-UX333FA-UX333FA systemd[1]:[COLOR=#daa520] virtualbox.service: Failed wit
h result 'exit-code'.[/COLOR]
Jun 27 21:10:58 ryanowns-ZenBook-UX333FA-UX333FA systemd[1]: [COLOR=#ff0000]Failed to start virtualbox.ser
vice - LSB: VirtualBox Linux kernel module.[/COLOR]
Setting up virtualbox (7.0.16-dfsg-2ubuntu1) ...
[COLOR=#ff0000]Job for virtualbox.service failed because the control process exited with error code.
See "systemctl status virtualbox.service" and "journalctl -xeu virtualbox.service" for deta
ils.[/COLOR]
invoke-rc.d: initscript virtualbox, action "restart" failed.
× virtualbox.service - LSB: VirtualBox Linux kernel module
     Loaded: loaded (/etc/init.d/virtualbox; generated)
     Active: [COLOR=#ff0000]failed [/COLOR](Result: exit-code) since Thu 2024-06-27 21:10:59 PDT; 11ms ago
       Docs: man:systemd-sysv-generator(8)
    Process: 15634 ExecStart=/etc/init.d/virtualbox start [COLOR=#ff0000](code=exited, status=1/FAILURE)[/COLOR]
        CPU: 45ms

Jun 27 21:10:59 ryanowns-ZenBook-UX333FA-UX333FA systemd[1]: Starting virtualbox.service - 
LSB: VirtualBox Linux kernel module...
Jun 27 21:10:59 ryanowns-ZenBook-UX333FA-UX333FA virtualbox[15634]:  * Loading VirtualBox k
ernel modules...
Jun 27 21:10:59 ryanowns-ZenBook-UX333FA-UX333FA virtualbox[15634]:  * modprobe vboxdrv fai
led. Please use 'dmesg' to find out why
Jun 27 21:10:59 ryanowns-ZenBook-UX333FA-UX333FA virtualbox[15634]:    ...fail!
Jun 27 21:10:59 ryanowns-ZenBook-UX333FA-UX333FA systemd[1]: virtualbox.service: Control pr
ocess exited, code=exited, status=1/FAILURE
Jun 27 21:10:59 ryanowns-ZenBook-UX333FA-UX333FA systemd[1]: [COLOR=#daa520]virtualbox.service: Failed wit
h result 'exit-code'.[/COLOR]
Jun 27 21:10:59 ryanowns-ZenBook-UX333FA-UX333FA systemd[1]: [COLOR=#ff0000]Failed to start virtualbox.ser
vice - LSB: VirtualBox Linux kernel module.[/COLOR]

.........................................................................

× virtualbox.service - LSB: VirtualBox Linux kernel module
     Loaded: loaded (/etc/init.d/virtualbox; generated)
     Active: failed (Result: exit-code) since Thu 2024-06-27 21:10:59 PDT; 1min 42s ago
       Docs: man:systemd-sysv-generator(8)
    Process: 15634 ExecStart=/etc/init.d/virtualbox start (code=exited, status=1/FAILURE)
        CPU: 45ms

Jun 27 21:10:59 ryanowns-ZenBook-UX333FA-UX333FA systemd[1]: Starting virtualbox.service ->
Jun 27 21:10:59 ryanowns-ZenBook-UX333FA-UX333FA virtualbox[15634]:  * Loading VirtualBox >
Jun 27 21:10:59 ryanowns-ZenBook-UX333FA-UX333FA virtualbox[15634]:  * modprobe vboxdrv fa>
Jun 27 21:10:59 ryanowns-ZenBook-UX333FA-UX333FA virtualbox[15634]:    ...fail!
Jun 27 21:10:59 ryanowns-ZenBook-UX333FA-UX333FA systemd[1]: virtualbox.service: Control p>
Jun 27 21:10:59 ryanowns-ZenBook-UX333FA-UX333FA systemd[1]: virtualbox.service: Failed wi>
Jun 27 21:10:59 ryanowns-ZenBook-UX333FA-UX333FA systemd[1]: Failed to start virtualbox.se>
~
..............................................................................

journalctl -xeu virtualbox.service
Jun 27 20:27:50 ryanowns-ZenBook-UX333FA-UX333FA systemd[1]: Starting virtualbox.service - LSB: VirtualBox Linux kernel module...
&#9617;&#9617; Subject: A start job for unit virtualbox.service has begun execution
&#9617;&#9617; Defined-By: systemd
&#9617;&#9617; Support: [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
&#9617;&#9617; 
&#9617;&#9617; A start job for unit virtualbox.service has begun execution.
&#9617;&#9617; 
&#9617;&#9617; The job identifier is 2056.
Jun 27 20:27:50 ryanowns-ZenBook-UX333FA-UX333FA virtualbox[7400]:  * Loading VirtualBox kernel modules...
Jun 27 20:27:50 ryanowns-ZenBook-UX333FA-UX333FA virtualbox[7400]:  * modprobe vboxdrv failed. Please use 'dmesg' to find out why
Jun 27 20:27:50 ryanowns-ZenBook-UX333FA-UX333FA virtualbox[7400]:    ...fail!
Jun 27 20:27:50 ryanowns-ZenBook-UX333FA-UX333FA systemd[1]: virtualbox.service: Control process exited, code=exited, status=1/FAILURE
&#9617;&#9617; Subject: Unit process exited
&#9617;&#9617; Defined-By: systemd
&#9617;&#9617; Support: [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
&#9617;&#9617; 
&#9617;&#9617; An ExecStart= process belonging to unit virtualbox.service has exited.
&#9617;&#9617; 
&#9617;&#9617; The process' exit code is 'exited' and its exit status is 1.
Jun 27 20:27:50 ryanowns-ZenBook-UX333FA-UX333FA systemd[1]: virtualbox.service: Failed with result 'exit-code'.
&#9617;&#9617; Subject: Unit failed
&#9617;&#9617; Defined-By: systemd
&#9617;&#9617; Support: [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
&#9617;&#9617; 
&#9617;&#9617; The unit virtualbox.service has entered the 'failed' state with result 'exit-code'.
Jun 27 20:27:50 ryanowns-ZenBook-UX333FA-UX333FA systemd[1]: Failed to start virtualbox.service - LSB: VirtualBox Linux kernel module.
&#9617;&#9617; Subject: A start job for unit virtualbox.service has failed
&#9617;&#9617; Defined-By: systemd
&#9617;&#9617; Support: [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
&#9617;&#9617; 
&#9617;&#9617; A start job for unit virtualbox.service has finished with a failure.
&#9617;&#9617; 
&#9617;&#9617; The job identifier is 2056 and the job result is failed.
Jun 27 20:42:59 ryanowns-ZenBook-UX333FA-UX333FA systemd[1]: Starting virtualbox.service - LSB: VirtualBox Linux kernel module...
&#9617;&#9617; Subject: A start job for unit virtualbox.service has begun execution
&#9617;&#9617; Defined-By: systemd
&#9617;&#9617; Support: [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
&#9617;&#9617; 
&#9617;&#9617; A start job for unit virtualbox.service has begun execution.
&#9617;&#9617; 
&#9617;&#9617; The job identifier is 2895.
Jun 27 20:42:59 ryanowns-ZenBook-UX333FA-UX333FA virtualbox[11457]:  * Loading VirtualBox kernel modules...
Jun 27 20:42:59 ryanowns-ZenBook-UX333FA-UX333FA virtualbox[11457]:  * modprobe vboxdrv failed. Please use 'dmesg' to find out why
Jun 27 20:42:59 ryanowns-ZenBook-UX333FA-UX333FA virtualbox[11457]:    ...fail!
Jun 27 20:42:59 ryanowns-ZenBook-UX333FA-UX333FA systemd[1]: virtualbox.service: Control process exited, code=exited, status=1/FAILURE
&#9617;&#9617; Subject: Unit process exited
&#9617;&#9617; Defined-By: systemd
&#9617;&#9617; Support: [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
&#9617;&#9617; 
&#9617;&#9617; An ExecStart= process belonging to unit virtualbox.service has exited.
&#9617;&#9617; 
&#9617;&#9617; The process' exit code is 'exited' and its exit status is 1.
Jun 27 20:42:59 ryanowns-ZenBook-UX333FA-UX333FA systemd[1]: virtualbox.service: Failed with result 'exit-code'.
&#9617;&#9617; Subject: Unit failed
&#9617;&#9617; Defined-By: systemd
&#9617;&#9617; Support: [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
&#9617;&#9617; 
&#9617;&#9617; The unit virtualbox.service has entered the 'failed' state with result 'exit-code'.
Jun 27 20:42:59 ryanowns-ZenBook-UX333FA-UX333FA systemd[1]: Failed to start virtualbox.service - LSB: VirtualBox Linux kernel module.
&#9617;&#9617; Subject: A start job for unit virtualbox.service has failed
&#9617;&#9617; Defined-By: systemd
&#9617;&#9617; Support: [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
&#9617;&#9617; 
&#9617;&#9617; A start job for unit virtualbox.service has finished with a failure.
&#9617;&#9617; 
&#9617;&#9617; The job identifier is 2895 and the job result is failed.
Jun 27 21:10:58 ryanowns-ZenBook-UX333FA-UX333FA systemd[1]: Starting virtualbox.service - LSB: VirtualBox Linux kernel module...
&#9617;&#9617; Subject: A start job for unit virtualbox.service has begun execution
&#9617;&#9617; Defined-By: systemd
&#9617;&#9617; Support: [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
&#9617;&#9617; 
&#9617;&#9617; A start job for unit virtualbox.service has begun execution.
&#9617;&#9617; 
&#9617;&#9617; The job identifier is 3822.
Jun 27 21:10:58 ryanowns-ZenBook-UX333FA-UX333FA virtualbox[15347]:  * Loading VirtualBox kernel modules...
Jun 27 21:10:58 ryanowns-ZenBook-UX333FA-UX333FA virtualbox[15347]:  * modprobe vboxdrv failed. Please use 'dmesg' to find out why
Jun 27 21:10:58 ryanowns-ZenBook-UX333FA-UX333FA virtualbox[15347]:    ...fail!
Jun 27 21:10:58 ryanowns-ZenBook-UX333FA-UX333FA systemd[1]: virtualbox.service: Control process exited, code=exited, status=1/FAILURE
&#9617;&#9617; Subject: Unit process exited
&#9617;&#9617; Defined-By: systemd
&#9617;&#9617; Support: [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
&#9617;&#9617; 
&#9617;&#9617; An ExecStart= process belonging to unit virtualbox.service has exited.
&#9617;&#9617; 
&#9617;&#9617; The process' exit code is 'exited' and its exit status is 1.
Jun 27 21:10:58 ryanowns-ZenBook-UX333FA-UX333FA systemd[1]: virtualbox.service: Failed with result 'exit-code'.
&#9617;&#9617; Subject: Unit failed
&#9617;&#9617; Defined-By: systemd
&#9617;&#9617; Support: [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
&#9617;&#9617; 
&#9617;&#9617; The unit virtualbox.service has entered the 'failed' state with result 'exit-code'.
Jun 27 21:10:58 ryanowns-ZenBook-UX333FA-UX333FA systemd[1]: Failed to start virtualbox.service - LSB: VirtualBox Linux kernel module.
&#9617;&#9617; Subject: A start job for unit virtualbox.service has failed
&#9617;&#9617; Defined-By: systemd
&#9617;&#9617; Support: [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
&#9617;&#9617; 
&#9617;&#9617; A start job for unit virtualbox.service has finished with a failure.
&#9617;&#9617; 
&#9617;&#9617; The job identifier is 3822 and the job result is failed.
Jun 27 21:10:59 ryanowns-ZenBook-UX333FA-UX333FA systemd[1]: Starting virtualbox.service - LSB: VirtualBox Linux kernel module...
&#9617;&#9617; Subject: A start job for unit virtualbox.service has begun execution
&#9617;&#9617; Defined-By: systemd
&#9617;&#9617; Support: [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
&#9617;&#9617; 
&#9617;&#9617; A start job for unit virtualbox.service has begun execution.
&#9617;&#9617; 
&#9617;&#9617; The job identifier is 4017.
Jun 27 21:10:59 ryanowns-ZenBook-UX333FA-UX333FA virtualbox[15634]:  * Loading VirtualBox kernel modules...
Jun 27 21:10:59 ryanowns-ZenBook-UX333FA-UX333FA virtualbox[15634]:  * modprobe vboxdrv failed. Please use 'dmesg' to find out why
Jun 27 21:10:59 ryanowns-ZenBook-UX333FA-UX333FA virtualbox[15634]:    ...fail!
Jun 27 21:10:59 ryanowns-ZenBook-UX333FA-UX333FA systemd[1]: virtualbox.service: Control process exited, code=exited, status=1/FAILURE
&#9617;&#9617; Subject: Unit process exited
&#9617;&#9617; Defined-By: systemd
&#9617;&#9617; Support: [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
&#9617;&#9617; 
&#9617;&#9617; An ExecStart= process belonging to unit virtualbox.service has exited.
&#9617;&#9617; 
&#9617;&#9617; The process' exit code is 'exited' and its exit status is 1.
Jun 27 21:10:59 ryanowns-ZenBook-UX333FA-UX333FA systemd[1]: virtualbox.service: Failed with result 'exit-code'.
&#9617;&#9617; Subject: Unit failed
&#9617;&#9617; Defined-By: systemd
&#9617;&#9617; Support: [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
&#9617;&#9617; 
&#9617;&#9617; The unit virtualbox.service has entered the 'failed' state with result 'exit-code'.
Jun 27 21:10:59 ryanowns-ZenBook-UX333FA-UX333FA systemd[1]: Failed to start virtualbox.service - LSB: VirtualBox Linux kernel module.
&#9617;&#9617; Subject: A start job for unit virtualbox.service has failed
&#9617;&#9617; Defined-By: systemd
&#9617;&#9617; Support: [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
&#9617;&#9617; 
&#9617;&#9617; A start job for unit virtualbox.service has finished with a failure.
&#9617;&#9617; 
&#9617;&#9617; The job identifier is 4017 and the job result is failed.
lines 91-132/132 (END)
&#9617;&#9617; The unit virtualbox.service has entered the 'failed' state with result 'exit-code'.
Jun 27 21:10:58 ryanowns-ZenBook-UX333FA-UX333FA systemd[1]: Failed to start virtualbox.se>
&#9617;&#9617; Subject: A start job for unit virtualbox.service has failed
&#9617;&#9617; Defined-By: systemd
&#9617;&#9617; Support: [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
&#9617;&#9617; 
&#9617;&#9617; A start job for unit virtualbox.service has finished with a failure.
&#9617;&#9617; 
&#9617;&#9617; The job identifier is 3822 and the job result is failed.
Jun 27 21:10:59 ryanowns-ZenBook-UX333FA-UX333FA systemd[1]: Starting virtualbox.service ->
&#9617;&#9617; Subject: A start job for unit virtualbox.service has begun execution
&#9617;&#9617; Defined-By: systemd
&#9617;&#9617; Support: [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
&#9617;&#9617; 
&#9617;&#9617; A start job for unit virtualbox.service has begun execution.
&#9617;&#9617; 
&#9617;&#9617; The job identifier is 4017.
Jun 27 21:10:59 ryanowns-ZenBook-UX333FA-UX333FA virtualbox[15634]:  * Loading VirtualBox >
Jun 27 21:10:59 ryanowns-ZenBook-UX333FA-UX333FA virtualbox[15634]:  * modprobe vboxdrv fa>
Jun 27 21:10:59 ryanowns-ZenBook-UX333FA-UX333FA virtualbox[15634]:    ...fail!
Jun 27 21:10:59 ryanowns-ZenBook-UX333FA-UX333FA systemd[1]: virtualbox.service: Control p>
&#9617;&#9617; Subject: Unit process exited
&#9617;&#9617; Defined-By: systemd
&#9617;&#9617; Support: [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
&#9617;&#9617; 
&#9617;&#9617; An ExecStart= process belonging to unit virtualbox.service has exited.
&#9617;&#9617; 
&#9617;&#9617; The process' exit code is 'exited' and its exit status is 1.
Jun 27 21:10:59 ryanowns-ZenBook-UX333FA-UX333FA systemd[1]: virtualbox.service: Failed wi>
&#9617;&#9617; Subject: Unit failed
&#9617;&#9617; Defined-By: systemd
&#9617;&#9617; Support: [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
&#9617;&#9617; 
&#9617;&#9617; The unit virtualbox.service has entered the 'failed' state with result 'exit-code'.
Jun 27 21:10:59 ryanowns-ZenBook-UX333FA-UX333FA systemd[1]: Failed to start virtualbox.se>
&#9617;&#9617; Subject: A start job for unit virtualbox.service has failed
&#9617;&#9617; Defined-By: systemd
&#9617;&#9617; Support: [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
&#9617;&#9617; 
&#9617;&#9617; A start job for unit virtualbox.service has finished with a failure.
&#9617;&#9617; 
&#9617;&#9617; The job identifier is 4017 and the job result is failed.
lines 91-132/132 (END)

---

### Post by khunguy on 2024-06-28
I have installed virtualbox-7.0_7.0.18.162988~....deb and Oracle_VM_VirtualBox_Etension pack

---

