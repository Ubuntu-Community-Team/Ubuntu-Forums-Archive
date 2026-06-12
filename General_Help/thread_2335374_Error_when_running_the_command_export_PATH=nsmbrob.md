---
title: "Error when running the command export PATH=/nsm/bro/bin:$PATH"
date: 2016-08-28
forum: General Help
---

### Post by ssh2 on 2016-08-28
I want to install BRO-IDS.

I did the following commands:

    cd bro-2.2
    ./configure --prefix=/nsm/bro
    make
    make install

When I run the following command:

    export PATH=/nsm/bro/bin:$PATH

Do not be operational.Is it correct?
How do I run this command?

    "You can also add PATH=/opt/bro2/bin:$PATH to your ~/.profile file in your home directory to make the change permanent."

I get the following error:

    root@ubuntu:/home/eng-it/bro-2.2# ~/.profile
    bash: /root/.profile: Permission denied

and for this:

    root@ubuntu:/home/eng-it/bro-2.2# sudo su -c "echo 'PATH=/opt/bro2/bin:$PATH'>>/etc/profile"

Do not be operational.

Is it correct?

---

### Post by Impavidus on 2016-08-28
> **ssh2 said:**
> I want to install BRO-IDS.

I did the following commands:

    cd bro-2.2
    ./configure --prefix=/nsm/bro
    make
    make installNot really the preferred way to install stuff, but if it's the only option you have, it's OK.

> When I run the following command:

    export PATH=/nsm/bro/bin:$PATH

Do not be operational.Is it correct?
How do I run this command?That command is correct. It adds the directory /nsm/bro/bin to your PATH, so that the shell will look in that directory to find your executable. Most commands don't give any output, unless there is an error message.

    > "You can also add PATH=/opt/bro2/bin:$PATH to your ~/.profile file in your home directory to make the change permanent."

I get the following error:

    root@ubuntu:/home/eng-it/bro-2.2# ~/.profile
    bash: /root/.profile: Permission deniedTo add a line to that file, open the file in your favourite text editor, add the line and save it. And don't do that while running as root, because it may make some files in your home directory root-owned, with all kinds of nasty consequences. Alternatively, you can use echo and a shell redirect like in the next quote. What you tried is executing your .profile, which is not possible.

> and for this:

    root@ubuntu:/home/eng-it/bro-2.2# sudo su -c "echo 'PATH=/opt/bro2/bin:$PATH'>>/etc/profile"

Do not be operational.

Is it correct?
That command should work, but, as before, shouldn't give any output. If it does give output, it did so because it didn't work. Check by reading the file /etc/profile. Does the last line say PATH=/opt/bro2/bin:$PATH? Then it worked.

---

