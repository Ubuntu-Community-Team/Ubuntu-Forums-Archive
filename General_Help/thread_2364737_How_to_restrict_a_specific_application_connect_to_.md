---
title: "How to restrict a specific application connect to internet"
date: 2017-06-27
forum: General Help
---

### Post by unityforever on 2017-06-27
Can i just set up something in one time, then i can forbid an application to access to Internet permanently. even after i reboot my computer.

On windows i can set it in firewall.

How to achieve that on ubuntu, counting on iptables? what's the command then?

Is there any better opinions?

Thanks

---

### Post by TheFu on 2017-06-27
And on Windows, it is trivial to get around this block - just rename the file or copy it to a different name.  Because of that hack, firewall rules aren't normally tied to specific files/programs. It is simply too easy to get around.

Unix systems are about providing power-to-the-people.  Preventing access to normal things is possible, but requires a compliant end-user.  That's fine, if you are the end-user and willing to restrict access.

So, you can setup a specific userid to be used, voluntarily, to run said program. Then you can use the built-in firewall to prevent whatever network access you like for that userid. Since the firewall is built-into the kernel, the user-interface chosen is up to you. Iptables is just 1 of the possible user interfaces on Ubuntu. You may use it if you like.

You could similarly use control-groups to limit access to the internet for a program. There are a number of ways to access those
* unshare - which will block **all** network access
* apparmor - you'll want a custom profile
* containers - with network restricted for the entire container.
* firejail - you'll want a custom profile
* manually (I suppose)
Each of these also require a compliant end-user, someone willing to run a script that sets up the necessary environment and runs it.

Only you can decide which is best for your situation.  There are reasons to use each method. Because I'm more familiar with firejail, I'd probably use that. But it isn't available on all supported versions of Ubuntu, so I might be forced to use containers or a firewall method on older LTS releases.

None of these options are 1-click.

With great power comes great responsibility.  That applies to nearly infinite flexibility, which is possible with Linux/Unix systems too.

A few links with more ideas and examples:
[https://www.linux.com/learn/lock-your-untrusted-applications-firejail](https://www.linux.com/learn/lock-your-untrusted-applications-firejail)
[https://unix.stackexchange.com/questions/68956/block-network-access-of-a-process](https://unix.stackexchange.com/questions/68956/block-network-access-of-a-process)

---

### Post by unityforever on 2017-06-29
thanks for your help.

im searching the information about applications you mentioned above.
i have to say linux and its extend tools is really powerful.
but they're a little bit complicated, need users have enough computer knowledge which may beyond many ordinary people have.
fortunately im good at that, but still feel tired doing those configuring.
maybe windows firewall is easy to bypass, but its strong enough for mortals... one click

---

