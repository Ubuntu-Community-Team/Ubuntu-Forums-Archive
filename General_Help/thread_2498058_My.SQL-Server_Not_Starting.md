---
title: "My.SQL-Server Not Starting"
date: 2024-05-28
forum: General Help
---

### Post by emmertjo on 2024-05-28
I am new to Linux in general and am trying to setup some software that requires MYSQL. I run through the steps, but it always fails to start the service. I am doing this on Ubuntu 24.04 under a fresh install.  Any help is greatly appreciated - I've been searching for hours and found other posts with similar issues, but most of them don't have solutions, or just say uninstall/reinstall, which I have done multiple times.

When I run ```
sudo systemctl start mysql.service
``` I receive ```
Job for mysql.service failed because the control process exited with error code.
See "systemctl status mysql.service" and "journalctl -xeu mysql.service" for details.

```

The results for the additional reports are:

```
$ systemctl status mysql.service
× mysql.service - MySQL Community Server
     Loaded: loaded (/usr/lib/systemd/system/mysql.service; enabled; preset: enabled)
     Active: failed (Result: exit-code) since Tue 2024-05-28 22:11:55 EDT; 42s ago
    Process: 3872 ExecStartPre=/usr/share/mysql/mysql-systemd-start pre (code=exited, status=1/FAILURE)
        CPU: 8ms

May 28 22:11:55 BMaxB2MiniPC systemd[1]: mysql.service: Scheduled restart job, restart counter is at 5.
May 28 22:11:55 BMaxB2MiniPC systemd[1]: mysql.service: Start request repeated too quickly.
May 28 22:11:55 BMaxB2MiniPC systemd[1]: mysql.service: Failed with result 'exit-code'.
May 28 22:11:55 BMaxB2MiniPC systemd[1]: Failed to start mysql.service - MySQL Community Server.


```

```
$ journalctl -xeu mysql.service
May 28 22:11:55 BMaxB2MiniPC systemd[1]: mysql.service: Control process exited, code=exited, status=1/FAILURE
&#9617;&#9617; Subject: Unit process exited
&#9617;&#9617; Defined-By: systemd
&#9617;&#9617; Support: http://www.ubuntu.com/support
&#9617;&#9617; 
&#9617;&#9617; An ExecStartPre= process belonging to unit mysql.service has exited.
&#9617;&#9617; 
&#9617;&#9617; The process' exit code is 'exited' and its exit status is 1.
May 28 22:11:55 BMaxB2MiniPC systemd[1]: mysql.service: Failed with result 'exit-code'.
&#9617;&#9617; Subject: Unit failed
&#9617;&#9617; Defined-By: systemd
&#9617;&#9617; Support: http://www.ubuntu.com/support
&#9617;&#9617; 
&#9617;&#9617; The unit mysql.service has entered the 'failed' state with result 'exit-code'.
May 28 22:11:55 BMaxB2MiniPC systemd[1]: Failed to start mysql.service - MySQL Community Server.
&#9617;&#9617; Subject: A start job for unit mysql.service has failed
&#9617;&#9617; Defined-By: systemd
&#9617;&#9617; Support: http://www.ubuntu.com/support
&#9617;&#9617; 
&#9617;&#9617; A start job for unit mysql.service has finished with a failure.
&#9617;&#9617; 
&#9617;&#9617; The job identifier is 17813 and the job result is failed.
May 28 22:11:55 BMaxB2MiniPC systemd[1]: mysql.service: Scheduled restart job, restart counter is at 5.
&#9617;&#9617; Subject: Automatic restarting of a unit has been scheduled
&#9617;&#9617; Defined-By: systemd
&#9617;&#9617; Support: http://www.ubuntu.com/support
&#9617;&#9617; 
&#9617;&#9617; Automatic restarting of the unit mysql.service has been scheduled, as the result for
&#9617;&#9617; the configured Restart= setting for the unit.
May 28 22:11:55 BMaxB2MiniPC systemd[1]: mysql.service: Start request repeated too quickly.
May 28 22:11:55 BMaxB2MiniPC systemd[1]: mysql.service: Failed with result 'exit-code'.
&#9617;&#9617; Subject: Unit failed
&#9617;&#9617; Defined-By: systemd
&#9617;&#9617; Support: http://www.ubuntu.com/support
&#9617;&#9617; 
&#9617;&#9617; The unit mysql.service has entered the 'failed' state with result 'exit-code'.
May 28 22:11:55 BMaxB2MiniPC systemd[1]: Failed to start mysql.service - MySQL Community Server.
&#9617;&#9617; Subject: A start job for unit mysql.service has failed
&#9617;&#9617; Defined-By: systemd
&#9617;&#9617; Support: http://www.ubuntu.com/support
&#9617;&#9617; 
&#9617;&#9617; A start job for unit mysql.service has finished with a failure.
&#9617;&#9617; 
&#9617;&#9617; The job identifier is 17913 and the job result is failed.

```

---

### Post by yancek on 2024-05-29
Doing an online search for the error you report "mysql.service: Start request repeated too quickly" shows a number of threads with suggestions.  You might try the suggestions at the links below if you haven't (you don't mention any specific efforts so we're guessing here).  The most frequent problem is there not being a /var/log/mysql directory so verify that directory exists and has correct owner:group permissions.

[https://stackoverflow.com/questions/57603349/errormysqld-service-start-request-repeated-too-quickly-on-manjaro](https://stackoverflow.com/questions/57603349/errormysqld-service-start-request-repeated-too-quickly-on-manjaro)

[https://stackoverflow.com/questions/72073953/mysql-cannot-start-in-ubuntu-22-04](https://stackoverflow.com/questions/72073953/mysql-cannot-start-in-ubuntu-22-04)

I'd suggest that if you are going online and following suggestions that you make note of what you have done and the results, failure, some improvement or whatever happened.  That way members here won't waste time/effort suggesting things you have already done.  It could also be useful for you in the future, particularly if you are making changes to configuration files, settings and owner:group permissions.  If you try something and it doesn't help, you can go back to the original settings.

---

### Post by Tadaen_Sylvermane on 2024-05-29
Open this file with a text editor. i us nano.

```
nano /usr/lib/systemd/system/mysql.service
```

What is the contents of the ```

ExecStartPre=
``` line? That is where the problem is according to the journalctl. It's the first error. That will tell you the first problem. Solve it, then try again until it starts. Otherwise you are just guessing.

---

