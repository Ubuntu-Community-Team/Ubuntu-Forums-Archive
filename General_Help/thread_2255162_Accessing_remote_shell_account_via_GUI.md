---
title: "Accessing remote shell account via GUI"
date: 2014-12-02
forum: General Help
---

### Post by t0p on 2014-12-02
I have a shell account on a remote server.  Running 12.04, I can log into the account with ssh via terminal.  Before 12.04 I was able to connect to the server using GUI (via file manager I think) and then could drag and drop files to and from the remote server and my computer (which automatically used sftp).  But I can't do that with 12.04.  I've tried Remmina Remote Desktop Client but I can't get it to work.  I set it up to connect via ssh, but when I input the password I get
```
SSH password authentication failed: Access denied. Authentication that can continue: publickey,password,keyboard-interactive,hostbased
```

I set it up to use sftp, but when I try to connect and input the password I get
```
SSH password authentication failed: Access denied. Authentication that can continue: publickey,password,keyboard-interactive,hostbased
```

In those error messages, it says "Authentication that can continue: ...password...". So what password is it on about?  I have my shell account set up so I log in with username and password, which, as I already said, works fine when using ssh command in terminal. Why won't it let me connect via Remmina?  Connecting with ssh through the terminal is not so useful, as I can't just transfer files from my computer to remote account and back as easily as drag and drop.  I have to email files from or to the remote shell account which is a pita.

So: why has accessing remote servers been removed from the file manager in Ubuntu?  Why can't I make Remmina work?  Is there another way I can drag and drop files to/from remote shell account?

Cheers.

---

### Post by papibe on 2014-12-02
Hi t0p.

That's is the way I usually access my server. The general functionality has not been removed, as it still works for me both on 12.04 and 14.04.

This is what I would do:
[LIST]
[*]Remove the credentials saved on the Keyring: Open 'Passwords and Keys', and delete the saved credentials on Passwords -> Login.
[*]Remove the bookmark, if exists, from Nautilus: Bookmarks -> Bookmarks.
[/LIST]
Then try to connect to your server again from Nautilus. I've been using this structure to connect BTW:
```
sftp://server:portnumber/path/to/home
```
Hope this points you in the right direction.

Let us know how it goes.
Regards.

---

### Post by t0p on 2014-12-02
Thanks for the response.  I have no credentials on my Keyring.  No bookmark in Nautilus as it seems to no longer have the Access Remote Server option it used to have before 12.04.  Not sure where you want me to put command [COLOR=#000000][FONT=Ubuntu Mono]sftp://server: portnumber/path/to/home.

Nautilus used to have an option to access remote servers.  But that seems to have gone now.  I don't know what the alternative is (apart from the terminal, and all I know about the terminal command is
```
ssh -l username server.com
```

I'm all confoozed...![/FONT][/COLOR]

---

### Post by t0p on 2014-12-02
I have now learnt how to do what I was wanting.  If I go into Nautilus (file manager) I find the ability to connect to remote server under **File > Connect to server**.  Opens a new window, into the file system of my shell account, and I can drag and drop files to it as before.

---

