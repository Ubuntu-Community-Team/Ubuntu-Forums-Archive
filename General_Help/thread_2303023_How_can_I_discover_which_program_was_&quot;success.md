---
title: "How can I discover which program was &quot;successfully installed&quot;?"
date: 2015-11-15
forum: General Help
---

### Post by Bobby_James on 2015-11-15
Is there a way from the command line to discover which programs were automatically installed?

I ask because I got a dialogue box (see attachment) which told me that "the update was successfully installed". Only I don't know what the update was. I don't recall updating.

Thanks.

---

### Post by snarkyCoder on 2015-11-15
If you go to the Ubuntu Software Center there is a **History** tab where you could look for that.

---

### Post by grahammechanical on 2015-11-15
What settings have you enabled in System Settings>Software & Updates>Updates tab?

If "When there are security updates" is set to "Download & Install automatically." Then it could be a security update but the default setting is "Display immediately."

Regards.

---

### Post by Bobby_James on 2015-11-15
> **grahammechanical said:**
> What settings have you enabled in System Settings>Software & Updates>Updates tab?

If "When there are security updates" is set to "Download & Install automatically." Then it could be a security update but the default setting is "Display immediately."

Regards.

It is "display immediately". I checked the history in software settings and it says the last installation was last Tuesday. However, I'm sure the message appeared on Friday last week.

Does the screenshot look authentic to you (i.e. what Ubuntu would normally look like when doing installations)

---

### Post by howefield on 2015-11-16
You could also try the log files, possibly a bit more verbose than Software Centre..

```
/var/log/apt/history.log
```
```
/var/log/apt/term.log
```

---

### Post by matt_symes on 2015-11-16
Hi

As well as the apt logs, as suggested by howefield, there is also the dpkg logs that will show every deb package installed.

If you're sure the update happened last Friday then this command will show you all the deb packages installed on that date.

```
egrep "**2015-11-13** [0-9:]{8} install" /var/log/dpkg.log
```

If you're not sure the update happened last Friday then change the date, highlighted in bold above, to the correct date you think the system was updated.

**EDIT:**

The above command does assume your dpkg logs have not been rotated since then.

Kind regards

---

### Post by vasa1 on 2015-11-16
> **matt_symes said:**
> Hi

As well as the apt logs, as suggested by howefield, there is also the dpkg logs that will show every deb package installed.

If you're sure the update happened last Friday then this command will show you all the deb packages installed on that date.

```
egrep "**2015-11-13** [0-9:]{8} install" /var/log/dpkg.log
```

...
Hi, that code doesn't work for me even though I have entries like this:```
2015-11-13 06:48:52 startup archives unpack
2015-11-13 06:48:58 upgrade libk5crypto3:amd64 1.12+dfsg-2ubuntu5.1 1.12+dfsg-2ubuntu5.2
2015-11-13 06:48:58 status half-configured libk5crypto3:amd64 1.12+dfsg-2ubuntu5.1
2015-11-13 06:48:58 status unpacked libk5crypto3:amd64 1.12+dfsg-2ubuntu5.1
2015-11-13 06:48:58 status half-installed libk5crypto3:amd64 1.12+dfsg-2ubuntu5.1
2015-11-13 06:48:59 status half-installed libk5crypto3:amd64 1.12+dfsg-2ubuntu5.1
2015-11-13 06:48:59 status unpacked libk5crypto3:amd64 1.12+dfsg-2ubuntu5.2
2015-11-13 06:48:59 status unpacked libk5crypto3:amd64 1.12+dfsg-2ubuntu5.2
2015-11-13 06:48:59 upgrade libgssapi-krb5-2:amd64 1.12+dfsg-2ubuntu5.1 1.12+dfsg-2ubuntu5.2
2015-11-13 06:48:59 status half-configured libgssapi-krb5-2:amd64 1.12+dfsg-2ubuntu5.1
2015-11-13 06:48:59 status unpacked libgssapi-krb5-2:amd64 1.12+dfsg-2ubuntu5.1
2015-11-13 06:48:59 status half-installed libgssapi-krb5-2:amd64 1.12+dfsg-2ubuntu5.1
2015-11-13 06:49:00 status half-installed libgssapi-krb5-2:amd64 1.12+dfsg-2ubuntu5.1
2015-11-13 06:49:00 status unpacked libgssapi-krb5-2:amd64 1.12+dfsg-2ubuntu5.2
2015-11-13 06:49:00 status unpacked libgssapi-krb5-2:amd64 1.12+dfsg-2ubuntu5.2
2015-11-13 06:49:00 upgrade libkrb5-3:amd64 1.12+dfsg-2ubuntu5.1 1.12+dfsg-2ubuntu5.2
2015-11-13 06:49:00 status half-configured libkrb5-3:amd64 1.12+dfsg-2ubuntu5.1
2015-11-13 06:49:01 status unpacked libkrb5-3:amd64 1.12+dfsg-2ubuntu5.1
2015-11-13 06:49:01 status half-installed libkrb5-3:amd64 1.12+dfsg-2ubuntu5.1
2015-11-13 06:49:01 status half-installed libkrb5-3:amd64 1.12+dfsg-2ubuntu5.1
2015-11-13 06:49:01 status unpacked libkrb5-3:amd64 1.12+dfsg-2ubuntu5.2
2015-11-13 06:49:01 status unpacked libkrb5-3:amd64 1.12+dfsg-2ubuntu5.2
2015-11-13 06:49:02 upgrade libkrb5support0:amd64 1.12+dfsg-2ubuntu5.1 1.12+dfsg-2ubuntu5.2
2015-11-13 06:49:02 status half-configured libkrb5support0:amd64 1.12+dfsg-2ubuntu5.1
2015-11-13 06:49:02 status unpacked libkrb5support0:amd64 1.12+dfsg-2ubuntu5.1
2015-11-13 06:49:02 status half-installed libkrb5support0:amd64 1.12+dfsg-2ubuntu5.1
2015-11-13 06:49:02 status half-installed libkrb5support0:amd64 1.12+dfsg-2ubuntu5.1
2015-11-13 06:49:02 status unpacked libkrb5support0:amd64 1.12+dfsg-2ubuntu5.2
2015-11-13 06:49:02 status unpacked libkrb5support0:amd64 1.12+dfsg-2ubuntu5.2
2015-11-13 06:49:02 upgrade krb5-locales:all 1.12+dfsg-2ubuntu5.1 1.12+dfsg-2ubuntu5.2
2015-11-13 06:49:02 status half-configured krb5-locales:all 1.12+dfsg-2ubuntu5.1
2015-11-13 06:49:02 status unpacked krb5-locales:all 1.12+dfsg-2ubuntu5.1
2015-11-13 06:49:03 status half-installed krb5-locales:all 1.12+dfsg-2ubuntu5.1
2015-11-13 06:49:03 status half-installed krb5-locales:all 1.12+dfsg-2ubuntu5.1
2015-11-13 06:49:03 status unpacked krb5-locales:all 1.12+dfsg-2ubuntu5.2
2015-11-13 06:49:03 status unpacked krb5-locales:all 1.12+dfsg-2ubuntu5.2
2015-11-13 06:49:04 startup packages configure
2015-11-13 06:49:04 configure libkrb5support0:amd64 1.12+dfsg-2ubuntu5.2 <none>
2015-11-13 06:49:04 status unpacked libkrb5support0:amd64 1.12+dfsg-2ubuntu5.2
2015-11-13 06:49:04 status half-configured libkrb5support0:amd64 1.12+dfsg-2ubuntu5.2
2015-11-13 06:49:04 status **installed** libkrb5support0:amd64 1.12+dfsg-2ubuntu5.2
2015-11-13 06:49:04 status triggers-pending libc-bin:amd64 2.19-0ubuntu6.6
2015-11-13 06:49:05 configure libk5crypto3:amd64 1.12+dfsg-2ubuntu5.2 <none>
2015-11-13 06:49:05 status unpacked libk5crypto3:amd64 1.12+dfsg-2ubuntu5.2
2015-11-13 06:49:05 status half-configured libk5crypto3:amd64 1.12+dfsg-2ubuntu5.2
2015-11-13 06:49:05 status **installed** libk5crypto3:amd64 1.12+dfsg-2ubuntu5.2
2015-11-13 06:49:05 configure libkrb5-3:amd64 1.12+dfsg-2ubuntu5.2 <none>
2015-11-13 06:49:05 status unpacked libkrb5-3:amd64 1.12+dfsg-2ubuntu5.2
2015-11-13 06:49:05 status half-configured libkrb5-3:amd64 1.12+dfsg-2ubuntu5.2
2015-11-13 06:49:05 status **installed** libkrb5-3:amd64 1.12+dfsg-2ubuntu5.2
...
```
But this works:```
05:36 PM ~ $ egrep "2015-11-13.* installed " /var/log/dpkg.log
2015-11-13 06:49:04 status installed libkrb5support0:amd64 1.12+dfsg-2ubuntu5.2
2015-11-13 06:49:05 status installed libk5crypto3:amd64 1.12+dfsg-2ubuntu5.2
2015-11-13 06:49:05 status installed libkrb5-3:amd64 1.12+dfsg-2ubuntu5.2
2015-11-13 06:49:06 status installed libgssapi-krb5-2:amd64 1.12+dfsg-2ubuntu5.2
2015-11-13 06:49:06 status installed krb5-locales:all 1.12+dfsg-2ubuntu5.2
2015-11-13 06:49:08 status installed libc-bin:amd64 2.19-0ubuntu6.6
05:37 PM ~ $ 

```And if someone doesn't like egrep, they can use grep -E.

Also, zgrep may help to look at archived files unless of course the old file has been removed depending on logrotate's settings.

---

### Post by matt_symes on 2015-11-16
Hi

> **vasa1 said:**
> Hi, that code doesn't work for me even though I have entries like this:```
2015-11-13 06:48:52 startup archives unpack
2015-11-13 06:48:58 upgrade libk5crypto3:amd64 1.12+dfsg-2ubuntu5.1 1.12+dfsg-2ubuntu5.2
2015-11-13 06:48:58 status half-configured libk5crypto3:amd64 1.12+dfsg-2ubuntu5.1
2015-11-13 06:48:58 status unpacked libk5crypto3:amd64 1.12+dfsg-2ubuntu5.1
2015-11-13 06:48:58 status half-installed libk5crypto3:amd64 1.12+dfsg-2ubuntu5.1
2015-11-13 06:48:59 status half-installed libk5crypto3:amd64 1.12+dfsg-2ubuntu5.1
2015-11-13 06:48:59 status unpacked libk5crypto3:amd64 1.12+dfsg-2ubuntu5.2
2015-11-13 06:48:59 status unpacked libk5crypto3:amd64 1.12+dfsg-2ubuntu5.2
2015-11-13 06:48:59 upgrade libgssapi-krb5-2:amd64 1.12+dfsg-2ubuntu5.1 1.12+dfsg-2ubuntu5.2
2015-11-13 06:48:59 status half-configured libgssapi-krb5-2:amd64 1.12+dfsg-2ubuntu5.1
2015-11-13 06:48:59 status unpacked libgssapi-krb5-2:amd64 1.12+dfsg-2ubuntu5.1
2015-11-13 06:48:59 status half-installed libgssapi-krb5-2:amd64 1.12+dfsg-2ubuntu5.1
2015-11-13 06:49:00 status half-installed libgssapi-krb5-2:amd64 1.12+dfsg-2ubuntu5.1
2015-11-13 06:49:00 status unpacked libgssapi-krb5-2:amd64 1.12+dfsg-2ubuntu5.2
2015-11-13 06:49:00 status unpacked libgssapi-krb5-2:amd64 1.12+dfsg-2ubuntu5.2
2015-11-13 06:49:00 upgrade libkrb5-3:amd64 1.12+dfsg-2ubuntu5.1 1.12+dfsg-2ubuntu5.2
2015-11-13 06:49:00 status half-configured libkrb5-3:amd64 1.12+dfsg-2ubuntu5.1
2015-11-13 06:49:01 status unpacked libkrb5-3:amd64 1.12+dfsg-2ubuntu5.1
2015-11-13 06:49:01 status half-installed libkrb5-3:amd64 1.12+dfsg-2ubuntu5.1
2015-11-13 06:49:01 status half-installed libkrb5-3:amd64 1.12+dfsg-2ubuntu5.1
2015-11-13 06:49:01 status unpacked libkrb5-3:amd64 1.12+dfsg-2ubuntu5.2
2015-11-13 06:49:01 status unpacked libkrb5-3:amd64 1.12+dfsg-2ubuntu5.2
2015-11-13 06:49:02 upgrade libkrb5support0:amd64 1.12+dfsg-2ubuntu5.1 1.12+dfsg-2ubuntu5.2
2015-11-13 06:49:02 status half-configured libkrb5support0:amd64 1.12+dfsg-2ubuntu5.1
2015-11-13 06:49:02 status unpacked libkrb5support0:amd64 1.12+dfsg-2ubuntu5.1
2015-11-13 06:49:02 status half-installed libkrb5support0:amd64 1.12+dfsg-2ubuntu5.1
2015-11-13 06:49:02 status half-installed libkrb5support0:amd64 1.12+dfsg-2ubuntu5.1
2015-11-13 06:49:02 status unpacked libkrb5support0:amd64 1.12+dfsg-2ubuntu5.2
2015-11-13 06:49:02 status unpacked libkrb5support0:amd64 1.12+dfsg-2ubuntu5.2
2015-11-13 06:49:02 upgrade krb5-locales:all 1.12+dfsg-2ubuntu5.1 1.12+dfsg-2ubuntu5.2
2015-11-13 06:49:02 status half-configured krb5-locales:all 1.12+dfsg-2ubuntu5.1
2015-11-13 06:49:02 status unpacked krb5-locales:all 1.12+dfsg-2ubuntu5.1
2015-11-13 06:49:03 status half-installed krb5-locales:all 1.12+dfsg-2ubuntu5.1
2015-11-13 06:49:03 status half-installed krb5-locales:all 1.12+dfsg-2ubuntu5.1
2015-11-13 06:49:03 status unpacked krb5-locales:all 1.12+dfsg-2ubuntu5.2
2015-11-13 06:49:03 status unpacked krb5-locales:all 1.12+dfsg-2ubuntu5.2
2015-11-13 06:49:04 startup packages configure
2015-11-13 06:49:04 configure libkrb5support0:amd64 1.12+dfsg-2ubuntu5.2 <none>
2015-11-13 06:49:04 status unpacked libkrb5support0:amd64 1.12+dfsg-2ubuntu5.2
2015-11-13 06:49:04 status half-configured libkrb5support0:amd64 1.12+dfsg-2ubuntu5.2
2015-11-13 06:49:04 status **installed** libkrb5support0:amd64 1.12+dfsg-2ubuntu5.2
2015-11-13 06:49:04 status triggers-pending libc-bin:amd64 2.19-0ubuntu6.6
2015-11-13 06:49:05 configure libk5crypto3:amd64 1.12+dfsg-2ubuntu5.2 <none>
2015-11-13 06:49:05 status unpacked libk5crypto3:amd64 1.12+dfsg-2ubuntu5.2
2015-11-13 06:49:05 status half-configured libk5crypto3:amd64 1.12+dfsg-2ubuntu5.2
2015-11-13 06:49:05 status **installed** libk5crypto3:amd64 1.12+dfsg-2ubuntu5.2
2015-11-13 06:49:05 configure libkrb5-3:amd64 1.12+dfsg-2ubuntu5.2 <none>
2015-11-13 06:49:05 status unpacked libkrb5-3:amd64 1.12+dfsg-2ubuntu5.2
2015-11-13 06:49:05 status half-configured libkrb5-3:amd64 1.12+dfsg-2ubuntu5.2
2015-11-13 06:49:05 status **installed** libkrb5-3:amd64 1.12+dfsg-2ubuntu5.2
...
```
But this works:```
05:36 PM ~ $ egrep "2015-11-13.* installed " /var/log/dpkg.log
2015-11-13 06:49:04 status installed libkrb5support0:amd64 1.12+dfsg-2ubuntu5.2
2015-11-13 06:49:05 status installed libk5crypto3:amd64 1.12+dfsg-2ubuntu5.2
2015-11-13 06:49:05 status installed libkrb5-3:amd64 1.12+dfsg-2ubuntu5.2
2015-11-13 06:49:06 status installed libgssapi-krb5-2:amd64 1.12+dfsg-2ubuntu5.2
2015-11-13 06:49:06 status installed krb5-locales:all 1.12+dfsg-2ubuntu5.2
2015-11-13 06:49:08 status installed libc-bin:amd64 2.19-0ubuntu6.6
05:37 PM ~ $ 

```And if someone doesn't like egrep, they can use grep -E.

Also, zgrep may help to look at archived files unless of course the old file has been removed depending on logrotate's settings.

That's odd as on 13th i installed cpuburn

```
matthew-laptop:/home/matthew:1 % egrep "2015-11-13 [0-9:]{8} install" /var/log/dpkg.log
2015-11-13 22:58:21 install cpuburn:amd64 <none> 1.4a-5
matthew-laptop:/home/matthew:1 % 
``` 

An amended command would be

```

egrep "2015-11-13 [0-9:]{8} status installed" /var/log/dpkg.log
```

and when i run that command i get...

```
matthew-laptop:/home/matthew:1 % egrep "2015-11-13 [0-9:]{8} status installed" /var/log/dpkg.log
2015-11-13 22:58:29 status installed man-db:amd64 2.6.7.1-1ubuntu1
2015-11-13 22:58:34 status installed cpuburn:amd64 1.4a-5
matthew-laptop:/home/matthew:1 % 
```

Thanks for pointing it out as i looks like the original command might just display manually installed packages and/or not dependencies.

I'll look into that.

**EDIT:**

Yep. That original command only displays newly installed packages and dependencies and not upgraded packages.

The original command was adapted from a specific use case i had but, in this case, is an insufficient command for the OP's use case.

Thanks vasa1.

Kind regards

---

### Post by vasa1 on 2015-11-16
> **matt_symes said:**
> ...
I'll look into that.
...
I'll check why I'm not seeing any output. Maybe I goofed?

Could it be that mysterious "locale" is set differently for you and me? Just guessing... but how could I check?
```
05:51 PM ~ $ egrep "2015-11-13 [0-9:]{8} install" /var/log/dpkg.log
05:56 PM ~ $ egrep "2015-11-13 [0-9:]{8} install" /var/log/dpkg.log.1
05:56 PM ~ $ 
```

BTW, in case anyone wants to look all *existing* dpkg.log files whether archived or not, this inelegant code works:```
cat /var/log/dpkg.log /var/log/dpkg.log.1 > ~/Desktop/all-dpkg.log && zcat /var/log/dpkg.log.[0-9]*.gz >> ~/Desktop/all-dpkg.log && grep " installed " ~/Desktop/all-dpkg.log > ~/Desktop/dpkg-installs.log
```

---

### Post by matt_symes on 2015-11-16
Hi vasa1

See my edit to my post above :D

I'm pretty sure that's what's happening.

**EDIT:**

BTW: This may be easier. They may not be in chronological order though.

```
{cat /var/log/dpkg.log{,.1} && zcat /var/log/dpkg.log.?.gz} | less
```


Kind regards

---

### Post by vasa1 on 2015-11-16
> **matt_symes said:**
> Hi vasa1

See my edit to my post above :D

I'm pretty sure that's what's happening.

Kind regards

Okay, thanks :)

Now to fix that other code I posted. I have more dpkg.log archives than it deals with :(

---

