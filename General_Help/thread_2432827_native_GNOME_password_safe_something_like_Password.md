---
title: "native GNOME password safe something like PasswordSafe"
date: 2019-12-09
forum: General Help
---

### Post by jason.jackal on 2019-12-09
Is there any native GNOME password safe that provides features like PasswordSafe? I am looking for a password safe for Linux/Ubuntu, and not sure what one I want to use. I noticed Password Safe uses Mono/C#; however, is here anything native to the Linux/Ubuntu/Gnome tool chain?

Thank you
JJ

---

### Post by TheFu on 2019-12-09
> **jason.jackal said:**
> Is there any native GNOME password safe that provides features like PasswordSafe? I am looking for a password safe for Linux/Ubuntu, and not sure what one I want to use. I noticed Password Safe uses Mono/C#; however, is here anything native to the Linux/Ubuntu/Gnome tool chain?

You can use the **ldd** tool to uncover the libraries used by any programs. For example, I use **keepassxc**.

```
$ ldd  /usr/bin/keepassxc|more
        linux-vdso.so.1 =>  (0x00007fff55114000)
        libQt5Svg.so.5 => /usr/lib/x86_64-linux-gnu/libQt5Svg.so.5 (0x00007f172c3f5000)
        libqrencode.so.3 => /usr/lib/x86_64-linux-gnu/libqrencode.so.3 (0x00007f172b961000)
        libQt5Concurrent.so.5 => /usr/lib/x86_64-linux-gnu/libQt5Concurrent.so.5 (0x00007f172c3ee000)
        libsodium.so.23 => /usr/lib/x86_64-linux-gnu/libsodium.so.23 (0x00007f172b70f000)
        libykpers-1.so.1 => /usr/lib/x86_64-linux-gnu/libykpers-1.so.1 (0x00007f172b4fd000)
        libargon2.so.0 => /usr/lib/x86_64-linux-gnu/libargon2.so.0 (0x00007f172b2f4000)
        libz.so.1 => /lib/x86_64-linux-gnu/libz.so.1 (0x00007f172b0da000)
        libQt5Network.so.5 => /usr/lib/x86_64-linux-gnu/libQt5Network.so.5 (0x00007f172c292000)
        libQt5Widgets.so.5 => /usr/lib/x86_64-linux-gnu/libQt5Widgets.so.5 (0x00007f172aa4d000)
        libQt5Gui.so.5 => /usr/lib/x86_64-linux-gnu/libQt5Gui.so.5 (0x00007f172a505000)
        libgcrypt.so.20 => /opt/keepassxc-libs/lib/x86_64-linux-gnu/libgcrypt.so.20 (0x00007f172a1e9000)
        libquazip5.so.1 => /usr/lib/x86_64-linux-gnu/libquazip5.so.1 (0x00007f1729fb9000)
        libQt5DBus.so.5 => /usr/lib/x86_64-linux-gnu/libQt5DBus.so.5 (0x00007f1729f3b000)
        libQt5Core.so.5 => /usr/lib/x86_64-linux-gnu/libQt5Core.so.5 (0x00007f1729a65000)
        libstdc++.so.6 => /usr/lib/x86_64-linux-gnu/libstdc++.so.6 (0x00007f17296e3000)
        libm.so.6 => /lib/x86_64-linux-gnu/libm.so.6 (0x00007f17293da000)
        libc.so.6 => /lib/x86_64-linux-gnu/libc.so.6 (0x00007f1729010000)
        libyubikey.so.0 => /usr/lib/x86_64-linux-gnu/libyubikey.so.0 (0x00007f17287d2000)
....

```
I'd always assumed it was using GTK+ (Gnome toolkit), but clearly I was wrong. It uses Qt, which is the toolkit used by KDE.  OTOH, I see it is using libyubikey, which I find very encouraging.  I need to look at leveraging my yubikeys for access into the password DB.

---

### Post by jason.jackal on 2019-12-09
> **TheFu said:**
> You can use the **ldd** tool to uncover the libraries used by any programs. For example, I use **keepassxc**.


Thank you for all the details and the recommendation of 'keepassxc'. I was looking at Gnome Keyring; however, I cannot tell if i can just save usernames and passwords for websites and/or devices.

Much appreciated.
JJ

---

### Post by TheFu on 2019-12-09
I need a cross-platform password DB and the kdbx files work on all platforms with compatible programs.

I put the kdbx file onto about 6 different systems using rsync nightly and whenever I make a change to it, I'll drop a new version into my nextcloud server, which replicates it to my android devices.  On android, I use droidkey or droidpass or keedroid ... something like that.  I'm not tied to a phone and often forget it at home or in the car.

My requirements for a password manager center around security and politics. I want NOTHING entered automatically. I always want to initiate any web logins manually. I don't want any web browser plugin since those have turned out to be highly non-secure.  Last thing I need is for some website to use javascript to change titles to many different domain logins, possibly tricking an addon to provide all the credentials for the top 50 cloudy web-apps.  Nobody is doing this yet and it isn't likely, until you are in a country or on someone else's network where they control the DNS too.  There is would be really easy to make happen.  No thanks.

---

### Post by jason.jackal on 2019-12-09
> **TheFu said:**
> I need a cross-platform password DB and the kdbx files work on all platforms with compatible programs.

I put the kdbx file onto about 6 different systems using rsync nightly and whenever I make a change to it, I'll drop a new version into my nextcloud server, which replicates it to my android devices.  On android, I use droidkey or droidpass or keedroid ... something like that.  I'm not tied to a phone and often forget it at home or in the car.

My requirements for a password manager center around security and politics. I want NOTHING entered automatically. I always want to initiate any web logins manually. I don't want any web browser plugin since those have turned out to be highly non-secure.  Last thing I need is for some website to use javascript to change titles to many different domain logins, possibly tricking an addon to provide all the credentials for the top 50 cloudy web-apps.  Nobody is doing this yet and it isn't likely, until you are in a country or on someone else's network where they control the DNS too.  There is would be really easy to make happen.  No thanks.

Eh... I never thought of that. Thank you for pointing that out.

---

### Post by TheFu on 2019-12-09
> **jason.jackal said:**
> Eh... I never thought of that. Thank you for pointing that out.

Password managers aren't just for passwords.
[https://blog.jdpfu.com/2011/03/25/101-uses-for-a-password-manager](https://blog.jdpfu.com/2011/03/25/101-uses-for-a-password-manager)
You can store lots of stuff inside them.
Password managers totally rock.

---

