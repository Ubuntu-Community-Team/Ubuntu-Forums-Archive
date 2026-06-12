---
title: "GEDIT, FTP, and network servers"
date: 2008-04-10
forum: General Help
---

### Post by hawkeye0203 on 2008-04-10
Hello all!  I'm not a complete infant to Ubuntu, but I think I need a little help in this area.  I am a web developer and have been using gEdit (Text Editor) to do all my work (I choose gEdit because I have created my own color scheme and altered the php.lang file to meet my needs).

I, am, however having problems with a few things.  I'll list them to make it most clear:

Scenario 1: I have connected to a local network server via FTP and I edit the files in gEdit, but gEdit will not save the file back to the server...  Is there a way to get gEdit to save a FTP file back to the server?

Scenario 2: How can I mount/connect to a server so applications like Filezilla can see it in my local directory structure?  I access another local network server through Samba and when I make a change to the file, I need to save it to my desktop in order for filezilla to upload it to the web server.

Thanks for all the help!

---

### Post by danwood76 on 2008-04-10
1. by default it wont let you connect to unsecure FTP, you can change this with the gconf editor by finding the gedit section and adding ftp to the list.

2. You can mount ftp shares by going to connect to server and typing the details in, this will mount it as samba shares are mounted.

---

### Post by philphil on 2008-04-12
just to clear that up for any noobs like myself:

1. run: gconf-editor from the terminal or F2
2. navigate to: apps-->gedit-2-->preferences-->editor-->save
3. double click on "writable_vfs_schemes"
4. click add
5. type "ftp" without the quotes
6. press ok
7. press ok

it should now be working :)

---

### Post by hawkeye0203 on 2008-04-14
sweet!  Thanks everyone!

---

