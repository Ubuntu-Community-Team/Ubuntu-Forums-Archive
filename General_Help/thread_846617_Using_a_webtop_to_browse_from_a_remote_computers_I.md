---
title: "Using a webtop to browse from a remote computers IP"
date: 2008-07-01
forum: General Help
---

### Post by garethsimpsonuk on 2008-07-01
Hello all,

here's my problem:

I have a dedi server in a data center which i use mainly as a torrent seedbox. I usually download the torrent file to my computer and then upload to the server.

Good trackers issue you with a .torrent file that is unique to you. Some not so good ones don't. Therefore I download the torrent to my computer, upload to the seed box and the seedbox isn't noticed by the tracker / the stats aren't added to my account.
My server has no GUI and therefore no VNC. I tried using SSH and links to login at the tracker, hoping my server IP would then be recognised with that account. I still don't know if it has worked yet.

A better solution would be to use something such as eyeOS ( a php based 'webtop' ). Basically this has an inbuilt browser so I could go to the tracker with that browser in a browser, download the .torrent file straight to the server and then open with flux.
This way the .torrent file is being assigned directly to that IP.
Would this work? Has anyone had experience with webtops. Is eyeOS the best.

This would also be handy for things like being at work where the nanny filter is on steroids. Would this help me get to my gmail account etc?

This seems the best solution to my problem, I was just wonderin if there's any flaws to my theory and what others opinions are.

Thanks,
Gareth

---

### Post by garethsimpsonuk on 2008-07-02
bump

---

### Post by garethsimpsonuk on 2008-07-03
bump

---

### Post by Gunman1982 on 2008-07-03
You can use the ssh connection to the server as a tunnel where your ssh opens a socks proxy locally. But I don't know if you have sufficient rights at work or wherever you want to surf from to change the proxysettings of your browser. And you still would have to transfer the .torrent file back to the server but it should be bound to the server ip.
Example to use ssh as socks proxy:
ssh -2 -c 3des -D 1080 user@host 
the connection is encryipted and the socks proxy accessible through localhost:1080
to open such a proxy without openening a shell on the server:
ssh -2 -N -f -c 3des -D 1080 user@host

---

### Post by garethsimpsonuk on 2008-07-03
well it doesn't matter about work. the main thing is using my home browser with my servers IP. That looks lke it would work. Do I then configure firefox ( in windows ) to use the proxy?

Although I don't quite understand the commands this seems like a much better option as opposed to installing a whole new php application just to use as a proxy. It gives me something to research so thanks.

---

