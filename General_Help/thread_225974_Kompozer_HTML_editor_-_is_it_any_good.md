---
title: "Kompozer HTML editor - is it any good?"
date: 2006-07-30
forum: General Help
---

### Post by rolf_lindberg on 2006-07-30
[http://kompozer.net/](http://kompozer.net/)

I found this site, but I am a bit sceptical at trying software I know nothing about since I don't know very much about linux/ubuntu yet. If something goes wrong I wouldn't know how to fix it. But I have found Nvu to be the best (easiest) HTML-editor that I have tried, only there are a lot of things not working as I would hope. I miss Dreamweaver and NetObjects Fusion from my old XP-environment. 

Has anyone tried this KompoZer software? Is it any good? They present it as "the unofficial bug-fix of Nvu", but I found someone when searching Google saying it is a fork of Mozilla Composer that isn't really working that well. 

If I don't get any replies I guess I will have to wrestle my mind into trying it, but I would really appreciate some feedback before doing something unknown to my system... So far I have stuck with the repositories and Automatix for installing software.

---

### Post by croak77 on 2006-07-30
There is no harm in trying something new.

---

### Post by adamkane on 2006-07-30
We Ubuntu users are constantly coming across new and wonderful alternatives to the old and wonderful working applications that we are already using.

Almost always these latest and greatest are just new ideas that haven't been developed yet, and the authors are looking for attention and positive feedback.

---

### Post by fabiwan on 2006-08-07
> We Ubuntu users are constantly coming across new and wonderful alternatives to the old and wonderful working applications that we are already using.KompoZer is just a bug-fix release of Nvu. If you're pleased with the way Nvu works, there is no reason to switch to KompoZer.

> Almost always these latest and greatest are just new ideas that haven't been developed yet, and the authors are looking for attention and positive feedback.Wow, I suppose that you're an experienced Nvu user and that you've tried KompoZer? Or at least that you've read KompoZer's progress status?

I'm the maintainer of the KompoZer project. There is no new idea nor any new feature in KompoZer, it's just a bugfix. I've proposed this as a patch for Nvu but Linspire didn't accept it (Nvu isn't developed any more), so I had to make another project *('Nvu and its logo are trademarks of Linspire Inc.')*. It's fully functional and more stable than Nvu, but it has a 0.x version number because I don't consider Nvu as ready for production use until some critical bugs get fixed.

This project will stop as soon as the new (xulRunner-based) generation of Mozilla Composer comes true; the goal is only to maintain a reliable, Gecko-based, wysiwyg HTML editor until that. And it's tri-licenced so all my bugfixes can later be reused in Mozilla Composer 2.

PS: Nvu and KompoZer use separate profile folders, so you can use both of them on the same box.

---

### Post by loell on 2006-08-07
wow, these are one of the rare occassions that a maintainer participates on a discussion in ubuntuforums on particular application, coincidence is a good thing.

---

### Post by abloylas on 2006-08-17
Is there a Kubuntu Dapper repository for Kompozer?

---

### Post by zhangweiwu on 2007-09-03
I just wish to say thank you for maintaining KompoZer and thank you for choosing a name that reflect your relationship with Mozilla Composer and thank you for caring about users (bugfixing) and yet do not try to fork a project simply because a developer or a company want to have something on their own. It's very nice to hear that you wish the fixes in KompoZer back to mozilla project.

I haven't see any progress on Mozilla Composer development. Maybe someone can enlighten me on what they have been doing that users cannot see, but I as a user feel they were not supporting users any more. It would be better Mozilla to either really open up it's entrance to collect improvements and participation on development of composer, or just get this project out of mozilla to form a standalone project, or anything they can do to make composer actively maintained and developed. Users do need a good wysiwyg HTML composer, they need a good one, not several ones each with different bugs and limitations. Unfortunately this happened in OSS world before (that a product fork a lot of versions to provide user a lot of alternatives with each have their own flaw and advantage). Until users really have at least one good composer, it wouldn't be wise to split resource availalbe on the FOSS world to create many alternatives. I am really glad fabiwan is doing things the way I appreciate.

Thanks and please keep it up!

---

