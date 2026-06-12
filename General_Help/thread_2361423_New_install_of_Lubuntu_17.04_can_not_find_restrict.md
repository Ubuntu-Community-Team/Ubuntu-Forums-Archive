---
title: "New install of Lubuntu 17.04 can not find restricted extra repo"
date: 2017-05-16
forum: General Help
---

### Post by ibmorjamn on 2017-05-16
Hello all, this new install is on my old gateway LT-20 , usb drive only.
first off I did try to follow the thread about my other problem which leads to this repo problem.
first off , firefox will not connect. Can not connect to server. I did get the network manager installed and it works.
Also in terminal it can not find the restricted repo . I have the iso on a stick but insynaptic it points to cd and asked for the physical adress.

---

### Post by Bucky Ball on 2017-05-16
You are absolutely sure you are online? Try this in a terminal.

```
sudo apt update
```

Does that go through problem free and back to a cursor or do you get errors towards the end or anywhere else? If you get errors, please post them here and please use code tags. 

While still in a terminal, try this:

```
ping google.com
```

Do you get a response or 'Host cannot be reached' or something like that?

Go to 'Software and Updates> Other Software tab' and make sure you have the CD option at the top there unticked as a source.

---

### Post by ibmorjamn on 2017-05-16
google returns "name or service not known"
apt-get returns " some index files failed to download. they have been ignored or old ones used instead."

---

### Post by oldos2er on 2017-05-16
Are you using a mirror? If so, try changing to the main server.

---

### Post by ibmorjamn on 2017-05-17
I don't know why I would be using a mirror unless I messed up something in setting up nm ?
I'm over it. Thanks for the help;
I pulled lubuntu off and installed Bodhi. Almost everything works. Midori however is not playing youtube video's and have yet to hear any sound.
I might install google chrome , any thoughts on that ?
This netbook is for my grandson so I have to get the sound  , mp3 and youtube working. Lol

---

### Post by Bucky Ball on 2017-05-17
Good luck with it. Be aware that these forums support the official Ubuntu flavours; Ubuntu, Kubuntu, Xubuntu, Edubuntu, Lubuntu, UbuntuGnome, Ubuntu Studio, Mythbuntu, Ubuntu Mate, Ubuntu Budgie and Ubuntu Kylin.

For anything else, you'd probably be better going directly to that distro's forum. There is Other OS forums here, but support could be slow.

Good luck.

PS: Everyone uses a mirror to get software, updates and upgrade, generally the main Ubuntu mirror, depending where you live. If you read my post thoroughly you'll note that I was talking about 'Software and Updates> Ubuntu Software> Download with'. Whatever you have selected in 'Download with' drop-down is the mirror you're using. If you're not using one, that would cause a major issue.

---

### Post by ibmorjamn on 2017-05-17
Thanks for helping. I don't mean to be rude at all. I had been working for days on the netbook trying to figure out how to install linux and through ubuntu forum and wiki it got me through with Google search.Rufus works. I'm not a terminal enthusiast but I did enjoy hacking .lmao

I know Bodhi I is not Ubuntu official but like so many others it is based on the latest and my other questions are basic (I did sign up for their forum)
I run mate on my desktop and this was my first netbook install along side XP It worked but lubuntu should have nm applet working. I guess I am lazy when it comes to linux but I have used it since around 07. Many distro's

---

