---
title: "Keeping A Program Always Running"
date: 2013-12-07
forum: General Help
---

### Post by deepak2001 on 2013-12-07
I have a server and I connect to it via PuttY.
The thing is that I use it for LTC mining.
I use CPUMiner but, when I close the PuttY window [Or Due To Timeout I Get Disconnected], the CPUMiner also closes.
Is there any way to keep the CPU Miner running?
Also, can I add my CPUMiner command to startup and if yes how?
My CPUMiner is stored in /opt/cpuminer-2.3.2

The CPUMiner initiation command or me is like this ./minerd --url=stratum+tcp://host.com:port --userpass=user.worker:pass

---

### Post by r-senior on 2013-12-07
You can use the nohup command (NO Hang UP) to leave the program running after you disconnect. Appending '&' puts the program into background so that you can type 'exit' to get out of the shell.

```
nohup ./minerd -url=... &
```

[http://www.cyberciti.biz/tips/nohup-execute-commands-after-you-exit-from-a-shell-prompt.html](http://www.cyberciti.biz/tips/nohup-execute-commands-after-you-exit-from-a-shell-prompt.html)
[http://www.thegeekstuff.com/2010/05/unix-background-job/](http://www.thegeekstuff.com/2010/05/unix-background-job/)

If you control the server, a longer term solution would be to set the service to create on startup on the server. The steps for doing so would depend on the server.

---

### Post by ian-weisser on 2013-12-07
So you want free, detailed, customized advice to make your money-making more efficient?

You must learn how to write Upstart jobs in /etc/init, or how to use any of the *screen*, *tmux*, *byobu*, or *retty* packages.

---

### Post by Lars Noodén on 2013-12-07
If your  app keeps shutting down on its own then you'll want to make an [upstart](http://upstart.ubuntu.com/cookbook/) job of it.

If you just want to be able to log in and out and check status and output then you want a terminal multiplexer like screen or tmux.  If you haven't used either, then I would recommend using tmux.  It's a cleaner rewrite and  is less complicated yet just as flexible.  [tmux](http://sourceforge.net/p/tmux/tmux-code/ci/master/tree/FAQ) is in the repository.  

To use tmux, just run it on the remote machine after you've connected with PuTTY or ssh.

```

tmux

```

Then start your application.  You are free then to disconnect or close your window.  To come back to the same session, log back into the remote machine and then re-attach to the existing tmux session.

```

tmux attach

```

You'll resume the session in progress.

---

### Post by deepak2001 on 2013-12-08
> **r-senior said:**
> You can use the nohup command (NO Hang UP) to leave the program running after you disconnect. Appending '&' puts the program into background so that you can type 'exit' to get out of the shell.

```
nohup ./minerd -url=... &
```

[http://www.cyberciti.biz/tips/nohup-execute-commands-after-you-exit-from-a-shell-prompt.html](http://www.cyberciti.biz/tips/nohup-execute-commands-after-you-exit-from-a-shell-prompt.html)
[http://www.thegeekstuff.com/2010/05/unix-background-job/](http://www.thegeekstuff.com/2010/05/unix-background-job/)

If you control the server, a longer term solution would be to set the service to create on startup on the server. The steps for doing so would depend on the server.

I did it, and I got ```
 nohup: ignoring input and appending output to `nohup.out'
```

Is it okay?

---

### Post by codemaniac on 2013-12-08
> **deepak2001 said:**
> I did it, and I got ```
 nohup: ignoring input and appending output to `nohup.out'
```

Is it okay?

It is okay, the terminal output will be redirected to file nohup.out as it has not been redirected to other file.

---

