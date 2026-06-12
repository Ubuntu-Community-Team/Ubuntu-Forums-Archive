---
title: "sort command"
date: 2015-01-30
forum: General Help
---

### Post by Langstracht on 2015-01-30
I am running two linux machines.

On one
```
sort -h
```
which I need runs fine.  On the other it returns the invalid option error message.

Does anyone know how I can either fix this or work around it?

TIA

---

### Post by steeldriver on 2015-01-30
What are the versions on the two machines? 

```

sort --version

```

the `-h` option is fairly new, I think. From the coreutils package changelog:

```

coreutils (**7.5-1**) unstable; urgency=low

  * new upstream version
    - fix ls -1 output error (Closes: #539476)
    - new program "stdbuf"
    - chroot adds --userspec and --groups
    - cp adds --reflink
[B]    - sort adds --human-numeric-sort
[/B]    - tail --follow uses inotify 
  * update package description (Closes: #535458)
  * tweak section and priority for mktemp package
  * conflict with package "timeout". I think coreutils timeout is just
    different enough that it shouldn't replace that package.

```

---

### Post by Langstracht on 2015-01-30
Thanks for your prompt response.

The versions are 7.4 and 8.5.

So I guess the different question is how do I force installation of the newer version?

Or, if I can't, is there some work around that I can use instead?

Tx again.

---

### Post by Elfy on 2015-01-30
What version of Ubuntu are you using? 

As far as packages.ubuntu.com is concerned everything other than 10.04 Server is older than 7.5-1

[http://packages.ubuntu.com/search?keywords=coreutils&suite=default&section=all&arch=any&searchon=names](http://packages.ubuntu.com/search?keywords=coreutils&suite=default&section=all&arch=any&searchon=names)

---

### Post by Langstracht on 2015-01-30
I am using 10.04.

Your not having answered either of my questions leads to believe that you are not prepared to propose a work-around and, unless I upgrade the OS, I am out of luck.

So I'll be off to see if I can solve this for myself.

Thanks for your help

---

### Post by Impavidus on 2015-01-30
You could try manually installing a more recent version of sort, including any supporting libraries, but this may be quite a hassle. And as 10.04 server edition only has 3 months of support left, it wouldn't be a bad idea to upgrade anyway.

BTW, questions are not always immediately answered because people may need more information to answer them.

---

### Post by QIII on 2015-01-30
> BTW, questions are not always immediately answered because people may need more information to answer them.

This.  It's part of diagnosis, since any given answer does not apply in all circumstances.  Open-ended, fact-finding questions are an indication that people are interested in helping.  Otherwise they just wouldn't bother.

---

### Post by Langstracht on 2015-01-30
I guess we're all different ...

If I were to respond to a post that contained questions I would either

1 wait until I "knew" the answers

or

2 if I felt compelled to respond without addressing the questions, I would at least add that I was getting/needing extra information, or didn't know or ...

Sorry, but I concluded a specific answer was forthcoming.

Meanwhile I've gotten a solution to my problem.

As for upgrading ... yeah I guess so.   Can not say I am relishing that task.

---

### Post by QIII on 2015-01-30
Those who answered could not possibly have had enough information from your post to immediately know the source of the issue, much less whether it could be fixed or worked around.  They did not "know" the answer because you had not provided enough information to provide a good picture of the problem.

When you visit a doctor about a pain in your knee, do you expect him to immediately tell you what is wrong?  Do you expect that he will ask you some questions to help him formulate a diagnosis?

When you go to your mechanic to complain about your engine running rough, do you expect him to immediately tell you why?  Do you expect him to look at the engine to formulate a diagnosis?

Did you not understand that the questions asked were intended to gather information?

As a service to the other members of the Forum community, would it be possible to share the solution you found?

---

### Post by mc4man on 2015-01-30
> **Langstracht said:**
> I am running two linux machines.

On one
```
sort -h
```
which I need runs fine.  On the other it returns the invalid option error message.

Does anyone know how I can either fix this or work around it?

TIA

Wow, such a nicely crafted question, chock full of info

> **QIII said:**
> 

As a service to the other members of the Forum community, would it be possible to share the solution you found?

What he (or anyone) may have done is see if a subsequent sort binary that supported -h would run on 10.04. It likely would only come down to libc6 version.

coreutils is mainly  a collection of binaries so no need to try to install another package, one can just extract the binary of interest from a .deb & test it.
If it works then it can be simply placed in a bin in PATH

This would be a prime candidate for 10.04 i386 - [https://launchpad.net/ubuntu/+source/coreutils/8.5-1ubuntu3/+build/1786788](https://launchpad.net/ubuntu/+source/coreutils/8.5-1ubuntu3/+build/1786788)

---

### Post by TheFu on 2015-02-01
It is hard to explain to people with limited subject knowledge that there isn't a quick answer and there may not be just 1 answer.  We could spend all day guessing what the issue was which would be frustrating for everyone.

It could have been 
* corrupt installation
* bad environment settings
* deleted files
* poster who lied, unknowingly, about the results.
or
* simply different versions of the software ... we still see questions here from really, really, really, old, unsupported Ubuntu versions.

So - knowing the extra information provided by all the responders above, I'd get a newer version of sort, copy it over, naming it something different sort.8.5 and then I'd create an alias to that specific version for the userids which need to use it.  Swapping out core utilities like this system-wide can break startup files for other programs, so it is important to leave the original exactly where it is.  Or OP could live dangerously.

See ... there really isn't a problem, just a misunderstanding by the OP.  The flexibility of Linux provides a solution.

In my career, I remember asking what I thought was a simple question from an "expert" at work.  Rather than answering, he'd ask 5 more questions and provide options. I found it frustrating - after all, it was a simple question deserving of a simple answer, right?  Skip ahead 5 years.  No people are coming to my office and asking me very hard questions, so I ask them a few questions for clarification. See, the tiny amount of info their question provided wasn't enough to provide an answer that didn't screw up their system completely, so I didn't want to risk a "yes/no" answer when the best answer is "often A, but sometimes B."  Skip ahead 5 more years - during a performance evaluation, my boss, SVP of Development, dinged me for not answering "simple questions quickly."  He knew 1 OS, but not the other 12 that we supported, so he wanted the answer for every OS that existed, without having the background to understand that answer.

The simple answer for why -h worked on 1 and not on the other is there can be different versions of every program on different systems - actually, different userids can point to different versions of programs too on the same system. In many environments, this is extremely likely. In other environments, it is completely unheard.

Oh ... and we can't read minds. ;)  I always assume the person asking would like to LEARN. If they just want the command to type - I'm not going to answer - use google and see how far that gets you.

---

