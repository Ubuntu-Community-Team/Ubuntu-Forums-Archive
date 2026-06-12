---
title: "Command to switch Breyl &lt;=&gt; Gnome"
date: 2007-01-05
forum: General Help
---

### Post by Ecthelion on 2007-01-05
I'm currently playingTremulous (great open-source online game).
I can start up and play the game without problem when beryl is enabled, but everything gets freezed when I want to stop playing.
When I choose gnome as window manager, I can stop playing fin, without freeze.

So now I'm looking for a command to switch from beryl to gnome so I can make a script which gets loaded first, changes to gnome and only then starts the game.
I mean of course without having to log out an back in again.
More as: Right klick beryl icon, choose window manager, gnome.
But then as a commandline command.

Greetz,
Ecthelion

---

### Post by raul_ on 2007-01-05
I didn't test it but maybe 
```

killall beryl-manager;
metacity --replace;
(etc etc)

```

When you want to get back to beryl just start it normally (or create another script):

```

beryl-manager
emerald --replace

```

---

### Post by Ecthelion on 2007-01-05
Thank you that works...
Too bad there's no option like beryl-manager --windowmanager=metacity or something.
But killing and replacing works.
I wonder why just replacing doesn't work though.

Oh, and no need to do emerald --replace, when you start up bery-manager he loads emerald by default.

Thanks for the quick reply!

---

### Post by Ecthelion on 2007-01-06
Another question...

When I put this in my script
[QUOTE=script]killall beryl-manager
metacity --replace
tremulous --quiet[/QUOTE]
Somehow It doesn't start.
When I then load beryl again, suddenly it starts.

I think this is because the commands get passed too soon, and that somehow it gets linked to beryl anyway.
Is there a command which gives a break between two commandos in a script?
I dunno, maybe wait 2 seconds before doing "tremulous --quiet" ?

---

### Post by raul_ on 2007-01-06
The script should be like this

```

kilall  beryl-manager;
metacity --replace;
tremulous --quiet;

```

Save it in a .sh file and then 

```

sudo chmod +x whatevernameyougaveit.sh

```

And you're good to go

---

### Post by Ecthelion on 2007-01-06
[QUOTE=raul_]The script should be like this

```
kilall beryl-manager; metacity --replace; tremulous --quiet;
```

Save it in a .sh file and then

```
sudo chmod +x whatevernameyougaveit.sh
```

And you're good to go[/QUOTE]

:) 

That's exactly how it looks like.
I already made it executable etc...

When I run this script, beryl get's killed and I get metacity.
I see that happen.
But nothing else happens, I mean, the game doesn't start.

When I then open a terminal and do
```
beryl-manager
```
Then beryl loads up. And a second later suddenly the game gets launched.
That's what I meant in the other post.
Sorry if I wasn't clear :KS 

What's funny is that when the game gets started that way, the computer doesn't freeze either.
So I've even tried to add "beryl-manager" in the script, but that didn't started either...

So somehow the script get's executed, but the commandos that are after "metacity --replace" only get in the memory but don't gt executed...
Until I start up beryl again, then everything suddenly get loaded again.

The thing I would like to try is to make a kind of 'break' in the script. So that the commands after "metacity --replace" only get executed after a second or two. That way I'm sure metacity get's loaded fully before trying to start something in it (the game).

I'm not really that familliar with script etc, so it could be that this is only wishfull thinking or fantasy, and that the error is somewhere else. Like being mad with the lamp when the light goes out, instead of noticing that there's a power breakdown :D . Please tell me if it is :mrgreen:  .

---

### Post by raul_ on 2007-01-06
```

killall beryl-manager;
metacity --replace && sleep 2;
tremulous --quiet;

```

---

### Post by Ecthelion on 2007-01-06
Thank!

That works!

Use the "sleep" commando... right... I could hit myself.

Thanks again!

---

