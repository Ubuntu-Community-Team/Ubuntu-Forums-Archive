---
title: "accidentally removed my Internet connection"
date: 2015-02-11
forum: General Help
---

### Post by peter176 on 2015-02-11
Hey guys,

i did this:

```
sudo apt-get remove build-essential libreadline-dev libssl-dev libpq5 libpq-dev libreadline5 libsqlite3-dev libpcap-dev openjdk-7-jre subversion git-core autoconf postgresql pgadmin3 curl zlib1g-dev libxml2-dev libxslt1-dev vncviewer libyaml-dev ruby1.9.3 ruby-dev
```

Now i dont have a connection anymore.
It says ```
The system network service is not compatible with this version
```

I wanted to reinstall the removed packages with a live-stick, but it didnt work.
Any ideas how i can fix this problem ?

Thanks

Ubuntu: 14.10 64bit

---

### Post by ian-weisser on 2015-02-11
I think you learned your lesson about apt's warning.

When you do **sudo apt-get install network-manager **, what is the output?
The output should include the list of packages you need.
You can, of course, save that list as a text file.

You cannot install packages from the LiveUSB. It doesn't have the packages.

You CAN boot from the LiveUSB to get a network connection,
Mount your HDD (thereby accessing your list),
Use apt-get with the -d (--download only) flag to obtain the correct packages on your USB's /var/cache/apt/archives ,
Copy those packages to /var/cache/apt/archives on the HDD,
Reboot into into the broken system,
And suddenly they are available to install now. Try the **sudo apt-get install network manager** command again.

A similar method using a different computer for the download is:
On another computer, download the list of packages from packages.ubuntu.com.
Save the packages to some media. Don't rename anything - exact names are important. 
Insert the media into the broken machine.
Copy the packages from the media into /var/cache/apt/archives.
And suddenly they are available to install now. Try the **sudo apt-get install network manager** command again.

---

### Post by sudodus on 2015-02-11
Did you remove the packages or are they still present? (Uninstalling is not the same thing as removing the packages.)

- If the packages are still present in your computer, you can try to reinstall without an internet connection. Run the corresponding ***apt-get*** command line with ***install*** instead of ***remove***. It works at least to reinstall several simple packages (but I haven't tried with your particular command line).

- If you removed the packages you need to get them somehow, maybe it would be easiest to reinstall the whole system (after saving your personal files).

-o-

I know it is possible to install without an internet connection, but I don't know the details. Let us hope someone will chip in and help you.

---

### Post by peter176 on 2015-02-11
Yes i learned my lesson... :P

Thanks for the advice,  fixed it.
I reinstalled the packages, but this didnt help.

Then I installed the network-manager and the connection works again!
The strange thing was, that the network-manager service worked before, even without the package O.o.

Thank you for your help. =)

---

