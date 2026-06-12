---
title: "Installing Frozen Bubble 2.0.0"
date: 2006-10-28
forum: General Help
---

### Post by terces on 2006-10-28
I've installed SDL_Pango, the patch, SDL_mixer, and SDL perl.

I compiled and installed Frozen Bubble 2.0.0 without any errors.

When I run frozen bubble, I get the error:

```
[SDL Init] Can't locate auto/SDL/IMGLoad.al in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.8.7 /usr/local/share/perl/5.8.7 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl .) at /usr/local/lib/perl/5.8.7/SDL/Surface.pm line 56
```

I tried to locate IMGLoad.al but it doesn't seem to exist.
The path to where it should be is included in @INC as shown:

```
amiracle@amiracle-ubuntu:~/frozen-bubble-2.0.0$ locate IMGLoad.al
amiracle@amiracle-ubuntu:~/frozen-bubble-2.0.0$ locate auto/SDL
/usr/lib/perl5/auto/SDL_perl
/usr/lib/perl5/auto/SDL_perl/SDL_perl.so
/usr/lib/perl5/auto/SDL_perl/SDL_perl.bs
/usr/lib/perl5/auto/SDL
/usr/lib/perl5/auto/SDL/autosplit.ix
```

Any ideas?

---

### Post by terces on 2006-10-28
Solved:

It seems that sdl_perl v. 1.20.3 from synaptic didn't install IMGLoad.al

I uninstalled that version through synaptic and then went to:

[http://zarb.org/~gc/t/SDL_perl-1.20.0.tar.gz](http://zarb.org/~gc/t/SDL_perl-1.20.0.tar.gz)

to grab an earlier version. 

I installed that and everything works great now.

---

### Post by digitalghost1 on 2006-10-29
> **terces said:**
> Solved:

It seems that sdl_perl v. 1.20.3 from synaptic didn't install IMGLoad.al

I uninstalled that version through synaptic and then went to:

[http://zarb.org/~gc/t/SDL_perl-1.20.0.tar.gz](http://zarb.org/~gc/t/SDL_perl-1.20.0.tar.gz)

to grab an earlier version. 

I installed that and everything works great now.


I have a request for you, if you could put in a step by step list of instructions how you got Frozen Bubbles to install that would be great! 
I am a complete Newb to Linux and Ubuntu so it would be appreciated.
Thanks for your time.

---

### Post by digitalghost1 on 2006-10-29
> **digitalghost1 said:**
> I have a request for you, if you could put in a step by step list of instructions how you got Frozen Bubbles to install that would be great! 
I am a complete Newb to Linux and Ubuntu so it would be appreciated.
Thanks for your time.

Nevermind I found out how to do it.
I have dapper and all the latest updates so all I did was run this line in Terminal:

sudo apt-get install frozen-bubble

Source:[http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_install_game_Frozen-Bubble](http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_install_game_Frozen-Bubble)

Then to start the Game go to Applications > Games > Frozen-Bubble

---

### Post by terces on 2006-11-07
Sorry I didn't get back soon enough.

When I installed it Frozen Bubble 2.0.0 wasn't in any repository I had...

All I really did was follow the Install instructions but I had to pull a different version of SDL_perl as stated earlier.

---

