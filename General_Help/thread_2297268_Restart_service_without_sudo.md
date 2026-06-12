---
title: "Restart service without sudo"
date: 2015-10-02
forum: General Help
---

### Post by linuxuser600 on 2015-10-02
I am working on a college project that requires me to be able to restart services like apache within a webpage. Basically I would like to use php to call a bash file that in returns starts, stops, or restarts a specified service. This works well on all other commands that does not require sudo. Because of security concerns I would not like apache to be apart of the sudoers file. Is there a script out there that gets around using sudo or is there a file that allows the www-html user to run specific commands without sudo privledges? I have spent days googling and trying to find an answer and have come up with nothing. Any help or a confirmation that it cannot be done is greatly appreciated.

---

### Post by ian-weisser on 2015-10-02
Must ask: Is this homework?

---

### Post by mikewhatever on 2015-10-02
Here you go: [https://askubuntu.com/questions/159007/how-do-i-run-specific-sudo-commands-without-a-password](https://askubuntu.com/questions/159007/how-do-i-run-specific-sudo-commands-without-a-password)

---

### Post by linuxuser600 on 2015-10-02
No this is not homework. One of the final classes in my college that I have to take is a project class. Basically the professor goes out and finds companies that need information technology solutions and puts the class into groups and we work with the company and create them whatever system that they need. My group is creating a web interface for a project called GAM and one of the things he wants to be able to do is start stop and restart certain services.

---

### Post by linuxuser600 on 2015-10-02
> **mikewhatever said:**
> Here you go: [https://askubuntu.com/questions/159007/how-do-i-run-specific-sudo-commands-without-a-password](https://askubuntu.com/questions/159007/how-do-i-run-specific-sudo-commands-without-a-password)

That looks promising. I didn't know it was that simple. I will try it tonight. Thanks for the replies.

---

### Post by Lars Noodén on 2015-10-02
In [sudoers](http://manpages.ubuntu.com/manpages/trusty/en/man5/sudoers.5.html) configuration, if you follow a program by empty double quotes "" then the user is prohibited from adding any parameters.  If the double quotes are left off, then any parameters are allowed.  If specific parameters are listed, then just those parameters can be used.  

The book "Sudo Mastery" by Michael W Lucas will cover all your options with sudo, if you have it at your library or can order it.  It's worth reading and addresses the topic the best I've seen so far.

---

### Post by linuxuser600 on 2015-10-02
So I ran "sudo visudo -f /etc/sudoers.d/services" in the terminal and added "www-data group@group-virtual-machine = (root) NOPASSWD: /etc/init.d/". With it I used php to run a basic test script to stop apache. It did not work, but once I change www-data to the username that I am using I can run the script fine without typing in a password. Any ideas on why this could be? The same php script runs other shell scripts fine so there should not be a problem with it.

> The book "Sudo Mastery" by Michael W Lucas will cover all your options  with sudo, if you have it at your library or can order it.  It's worth  reading and addresses the topic the best I've seen so far.
I will have to check that book out. It sounds like it is a good read.

---

### Post by Lars Noodén on 2015-10-03
I'd look at the "group@group-virtual-machine" part and make sure it is something that fits the user www-data.

---

### Post by linuxuser600 on 2015-10-03
> **Lars Noodén said:**
> I'd look at the "group@group-virtual-machine" part and make sure it is something that fits the user www-data.

Thanks! That was it. I changed it to group-virtual-machine and now I can restart services within my php file. I cannot use the php file to call a shell script to run the same script for some reason though. But honestly I think this is good enough for what the company wants. Thanks for the help.

---

