---
title: "Authentication issues when launching Cubic"
date: 2020-06-23
forum: General Help
---

### Post by anon5710 on 2020-06-23
Hello,

I'm in the process of setting up a custom ubuntu iso with the help of CUBIC.
While it was working before (2 moths ago) now i cannot start it up anymore.


Nothing happens when I try to start Cubic from the "start menu"

When starting from the console :

> USER2@SkyDiver-138:~/Desktop$ cubic
Cubic (Custom Ubuntu ISO Creator) is a graphical user interface application and should be run using the application launcher. See "man cubic" for more information.

==== AUTHENTICATING FOR cubic ===
Enter superuser password to start Cubic
Multiple identities can be used for authentication:
 1.  USER1,,, (vagrant)
 2.  USER2
Choose identity to authenticate as (1-2): 2
Password: 
polkit-agent-helper-1: pam_authenticate failed: Authentication failure
==== AUTHENTICATION FAILED ===


USER2@SkyDiver-138:~/Desktop$ cubic
Cubic (Custom Ubuntu ISO Creator) is a graphical user interface application and should be run using the application launcher. See "man cubic" for more information.

==== AUTHENTICATING FOR cubic ===
Enter superuser password to start Cubic
Multiple identities can be used for authentication:
 1.  USER1,,, (vagrant)
 2.  USER2
Choose identity to authenticate as (1-2): 1
Password: 
polkit-agent-helper-1: error response to PolicyKit daemon: GDBus.Error:org.freedesktop.PolicyKit1.Error.Failed: No session for cookie
==== AUTHENTICATION FAILED ===
Error executing command as another user: Not authorized



I am sure about the root password, both users should be part of the wheel/sudo group.

---

### Post by anon5710 on 2020-06-23
So the solution found here [https://answers.launchpad.net/cubic/+question/688898](https://answers.launchpad.net/cubic/+question/688898) works.

[COLOR=#333333][FONT=Ubuntu]Try to use a tty PolicyKit agent instead...[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]    1. Open a terminal, execute the following, and note the resulting PID:[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]        echo $$[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]    2. Open a SECOND terminal and execute the following:[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]        pkttyagent --process <PID FROM STEP 1>[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]    3. In the FIRST terminal, execute the following:[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]        pkexec /usr/share/cubic/cubic.py "/usr/share/cubic"[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]    4. Return to the SECOND terminal and enter your sudo password when prompted.[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]        You should see output like the following in the SECOND terminal...[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]            pkttyagent --process <PID FROM STEP 1>
            ==== AUTHENTICATING FOR cubic ===
            Enter superuser password to start Cubic
            Authenticating as: Arjun Vikram,,, (arjvik)
            Password:
            ==== AUTHENTICATION COMPLETE ===[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]    5. The Cubic GUI should launch from the FIRST terminal.


Any idea how to make this permenant without setting it up ?[/FONT][/COLOR]

---

### Post by tea for one on 2020-06-23
If you upgrade Cubic to the latest version, you no longer have to authenticate with your admin password.

[https://answers.launchpad.net/cubic/+question/691143](https://answers.launchpad.net/cubic/+question/691143)

---

