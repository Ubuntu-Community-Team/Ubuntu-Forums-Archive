---
title: "Packages to compile"
date: 2013-12-24
forum: General Help
---

### Post by Tristan_Williams on 2013-12-24
This is just a curiosity question.

I know that compiling packages from source gives you software that is optimized for your particular system.

I am just wondering, what packages would it be most beneficial for me to compile from source, rather than just install binaries?

I was thinking along the lines of Xfce4 and Firefox.

What do you all think?

---

### Post by claracc on 2013-12-24
I think that you are going to encounter many problems compiling from source, please see this interesting link: [http://www.maximumpc.com/article/howtos/howto_compile_programs_from_source_linux](http://www.maximumpc.com/article/howtos/howto_compile_programs_from_source_linux) , for the advantages you can get.

 Also, nowadays there is not reason to compile software since hardware is better and quick, about software, if you want the newest you have repositories with backports that you can try.

---

### Post by Impavidus on 2013-12-24
What you get from the repositories has already been compiled to be optimised for your amd64-compatible processor (at least, most of us have such a processor) and your Ubuntu version. If you want even more optimisation it will require a lot of specialist work, apart from the usual difficulty of compiling from source. Not worth the effort, I'd say.

---

### Post by Tristan_Williams on 2013-12-24
I know I'll have problems with compiling. I've been compiling packages for my (attempter) Linux from Scratch system.
I would only be compiling on my "Testing" maching

---

### Post by oldos2er on 2013-12-24
Some source code is easier to compile than others; usually it's just a matter of installing all the necessary *-dev dependencies, and figuring out any configuration options you may want.

I would guess compiling a custom kernel would offer the most benefits, followed by the programs you mentioned.

---

### Post by oldos2er on 2013-12-24
Some source code is easier to compile than others; usually it's just a matter of installing all the necessary *-dev dependencies, and figuring out any configuration options you may want.

I would guess compiling a custom kernel would offer the most benefits, followed by the programs you mentioned. Whether those benefits would be noticeable or not I can't say.

---

### Post by Tristan_Williams on 2013-12-24
I have noticed a HUGE benefit from compiling a custom kernel.
I removed support for absolutely everything except what i actually use (i.e. Amature radio support) and it made things SOOOOO much faster.

I also noticed quite a large benefit from compiling Xfce4 and all of its extras, and firefox helped a lot too.

The ones I didnt notice a difference in was xfwm (I thought it would make a huge difference, but no...)

---

### Post by monkeybrain20122 on 2013-12-24
Well for software that is not in the repo or software which is broken, or old in the repo I would compile. I compile vlc e.g, as the repo version is not up to date and I want a new feature (vdpau)  Or, say, minitube, the repo version is completely broken due to it being too old.  There is an up to date version in the Software Center that costs $4. I wouldn't mind paying for it if I really use it, but I don't, so I grab the source and compiled just out of curiosity, that one is really easy to compile. 

In general I prefer to compile multimedia stuffs as the repo versions are often old or crippled in some ways (e.g k3b doesn't rip dvd because repo version is not compiled against libdvdread for some bureaucratic reasons) Other things I compiled are pspp (repo version too old) and octave 3.7 (developmental version) and a few other third party stuffs not in the repo.

I compiled gcc 4.4 last week on Saucy just because I want to build something that wouldn't work with the new compiler. Then after much work (it does work) I realised it is in the repo and I can easily switch between it and the default compiler (I build it locally)  Could have saved many hours. :)

---

### Post by monkeybrain20122 on 2013-12-24
> **Impavidus said:**
> What you get from the repositories has already been compiled to be optimised for your amd64-compatible processor (at least, most of us have such a processor) and your Ubuntu version. If you want even more optimisation it will require a lot of specialist work, apart from the usual difficulty of compiling from source. Not worth the effort, I'd say.

Not really. For system stuffs I can believe that, but for some end user software (multiverse?) I have the feeling that they just dump it there if they build it successfully so they can say 'hey we have it' and then forget about it, sometime the repo version is completely broken you wonder why it is even there. 

And if you use LTS everything in the repo is hopelessly out of date (they don't even update default software in point releases) so in those cases if you want newer versions you have to 1) find a ppa or 2) find a .deb download or 3) compile

---

