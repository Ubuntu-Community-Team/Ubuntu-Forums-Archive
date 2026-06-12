---
title: "Ares using Wine"
date: 2005-10-30
forum: General Help
---

### Post by daahli on 2005-10-30
Hey,

I just installed wine and tried to get the new version of Ares working. I was wondering whether anybody managed to get it working properly. It installs fine, but I then get an error message in wine that:

ws2_32.dll.getaddrinfo is unimplemented

And Ares refuses to connect. I did a websearch and apparently there are 2 solutions to the ws2_32.dll.getaddrinfo problem:

1) run wine emulating WIN98
2) use the patch available here: [http://bugs.winehq.org/attachment.cgi?id=1228&action=view](http://bugs.winehq.org/attachment.cgi?id=1228&action=view)

Unfortunately I was not able to figure out how to do 1), and I don't know where to put the patch (2). 

I'd really appreciate some help. Thanks!

---

### Post by munkymonkjr on 2005-10-30
i have not tried running Ares in a while, but a few months back i had it running fine. Make sure you're trying to run Ares LITE, Regular will not work right, and the media player will be down right useless anyway. 


that said, why not use a native P2P client?

---

### Post by daahli on 2005-10-30
hey,

If I'm not mistaken the Lite versions are discontinued since Ares became open source. I was able to find an old lite version, but I encountered the exact same error. Do you have any idea how to do either (1) or (2) of my original post?

I want to use Ares because for some reason the packet shaper at my college does not block Ares, but it does block every other network I've tried (Gnutella, G2, Edonkey, Kad, etc.). I actually just found out about this today. I'm not familiar with the Ares protocol, so I'm not really sure why this is the case. Please enlighten me if you think you might know the reason for this.

Thanks :)

---

### Post by desheikh on 2005-12-18
Hey.. Its the same at my Uni.. Ares is the only P2P which works :P.. the other P2P arent blocked but their bandwidths been cut down to the size of a pinhole :@... you wouldnt happen to be in NUS by any chance would you? :P

Try this link..
[http://frankscorner.org/index.php?p=areslite](http://frankscorner.org/index.php?p=areslite)
Use the given version of wine and ares should work fine.. use the lite version if you can get it but i think that regular version will work fine too..

Or you could try using the gift daemon and frontend like apollon(for kde, theres one for gnome too.. cant remember name).. its a bit tricky to setup but i think there are packages available on the repo now.. 
I had a problem getting an updated nodes list for it... I copied over the updated nodes from Kceasy(windows) and it worked fine!

---

### Post by dethdeks on 2007-07-16
im using ares while on wine mind u im using ares 1.9.9.3019 but i had an issue with the unicode in letters only showing up as "<<<<<<" instead of there names, but iv seem to have fixed that some how and now it shows the names in the chat proper but just not in the user list. it still how ever doesnt show emotes. or background colors if there is any in the motd.

---

