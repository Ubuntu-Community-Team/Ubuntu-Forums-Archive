---
title: "[SOLVED] Removal of Automatix"
date: 2007-08-04
forum: General Help
---

### Post by samurailink3 on 2007-08-04
I've been hearing bad things about automatix as of late, and I was wondering if there is any way to undo the potential damage it has done so when October rolls around, I can upgrade to 7.10 without too much hassle. I'm comfortable using synaptic. Is all it would take is removing automatix itself? Or removing all the programs/codecs that were installed by it? Thanks for the insight!

---

### Post by apetresc on 2007-08-04
> **samurailink3 said:**
> I've been hearing bad things about automatix as of late, and I was wondering if there is any way to undo the potential damage it has done so when October rolls around, I can upgrade to 7.10 without too much hassle. I'm comfortable using synaptic. Is all it would take is removing automatix itself? Or removing all the programs/codecs that were installed by it? Thanks for the insight!

Most of the problems with Automatix are pretty "instant-effect." If you have been using it without any visible problems, it is probably enough simply to remove it through apt, and forget about it.

There's no real need to remove the packages it has gotten you since, when it does happen to work, it does mostly the same thing you would've done manually yourself to get those packages installed.

---

### Post by w4ett on 2007-08-04
The command is:

```
sudo apt-get remove automatix2
```

Whatever you loaded via Automatix will remain, only the automatix install script will be removed

---

### Post by MrFSL on 2007-08-04
> I've been hearing bad things about automatix as of late, 
I find it unfair to announce this and, in so doing, help spread FUD without making clear what you "heard" that was so bad. Give the developers a break and avoid such unfriendly and inflammatory remarks.

---

### Post by Whoopie on 2007-08-04
[http://mjg59.livejournal.com/77440.html](http://mjg59.livejournal.com/77440.html)

---

### Post by samurailink3 on 2007-08-04
@ Whoopie, That's the exact article I read about it.
@MrFSL, I'm not saying it did cause problems, I'm just saying that I've heard things. I personally like automatix, I think it makes things faster when you first set up a box. My concern was that it would effect my upgrade to 7.10 in the coming months. I've heard that the concerns were FUD, I was just asking for opinions on the matter.
@AdrianP and w4ett, Thanks for the help, I didn't know if the 'problems' being described by various blogs were things that would happen slowly or right away. Now I now. Thanks for the help!  :)

---

### Post by apetresc on 2007-08-04
> **MrFSL said:**
> I find it unfair to announce this and, in so doing, help spread FUD without making clear what you "heard" that was so bad. Give the developers a break and avoid such unfriendly and inflammatory remarks.

MrFSL, with all due respect, our wariness with regards to Automatix is not "FUD". I, at least, have no vested interest in either promoting or attacking Automatix or its developers. The simple fact of the matter is: it DOES cause problems. Tons of them, and many of them are quite serious. This is not a judgement call, it is fact. If you want some proof, read the article linked earlier in this thread -- that is the opinion of the TECHNICAL review board, and it is *very* thoroughly backed up in that post.

Spend a few days on #ubuntu or #kubuntu reading some of the problems that pop up and you will agree that Automatix is not the best implementation in the world of what it's trying to do.

---

### Post by MrFSL on 2007-08-05
@AdrianP
> 've been hearing bad things about automatix as of late, and I was wondering if there is any way to undo the potential damage it has done...

This statement is, in and of itself... quite inflammatory in that it neither sites and professional evaluation nor specific link. To a user that has never used Automatix this statement serves to spread; Fear, Uncertainty, and Doubt. 

As to whether Automatix is, or is not good software; I did not comment. I requested that a user on this forum site their specific issue in the future so that others might be able to make better decisions either FOR or AGAINST using a piece of software. Siting specific issues allows developers to make corrections. Saying something is crap encourages developers like myself not to fix a darned thing!

According to the Automatix website:
> Automatix is free software; you can redistribute it and/or **MODIFY** if under the terms of the GNU...
By siting specific concerns and issues users can make changes/bug fixes as is the spirit of all open source software.

Lastly, Automatix has gotten a bad rap IMHO. It is more of a hack and unlike the article seems state; I don't feel that it tries to be a package manager at all. Nowhere does Automatix claim to be better then nor take the place of any other software. It is a tool, cobbled together by some hard working folks, which is aimed at helping people with some otherwise complex tasks. There is even a disclaimed to its effectiveness. 

As far as the article states, I only find 2% of the listed issues to be worthwhile or interesting. The rest simply does not speak to the potential danger of using this software and would be transparent to the novice user (to which this software might be particularly interesting.) 

I neither promote nor discourage the use of Automatix. I do, however, HIGHLY discourage the spreading of unsubstantiated FUD; _***caused by not siting specific examples is our posts***_.

---

### Post by apetresc on 2007-08-05
Are you serious? The user was not making a public statement about Automatix. He was asking how to remove it (in a SUPPORT FORUM) and gave a reason for why he wanted to do such a thing. You honestly believe he has to cite reasons for his own personal decisions? He has to justify them to you?

There's a difference between a company, upon whose opinion many people base their decision on, giving incomplete or misleading information aimed to confuse (the FUD you speak of), and a guy in a forum going "Hey guys, I want to remove automatix because I heard it can be harmful, how should I go about doing this?" If you actually want him to justify that personal opinion by citing it (especially considering that the main reason for this opinion *was posted on Slashdot today*), you are being very, very unreasonable.

I get the Open Source ideology. I'm a developer too. But expecting a user, asking a question about how to remove something on a **technical support** forum, to not only cite his reasons for wanting to remove it, but actually **berating him publicly for not modifying the program** which he wants to remove so that he would not be unsatisfied with it, is ridiculous.

And if you do not see the reasons why this tool might be VERY DANGEROUS, I posit that you may not really know what you are talking about. Just offhand,
[LIST=1]
[*] It modifies fstab and uses device names instead of UUID's. This can cause unbootable systems under some configurations.
[*] There are a lot of circumstances under which it could conflict with currently running package managers and mess up apt archives.
[*] Forces package removals which can in some circumstances will remove packages the user didn't intend to remove, not only without their permission, but without their knowledge (unless they were carefully reading Automatix output, which is unreasonable to expect)
[*] Will happily remove user-installed files that aren't registered with apt, files that Automatix had no hand in creating.
[/LIST]
And I'm just listing things off the top of my head here.


At any rate, even if none of these issues existed, and if Automatix were a perfectly safe and wonderful tool (it's not), it is **still** not okay to publicly berate a user asking how to remove a program on a support forum for not (a) Citing his reasons for doing so (b) Fixing the program themselves.

---

### Post by samurailink3 on 2007-08-05
Not trying to spread FUD, just wondering the general opinions of the people in the forums. Anyway, thanks for the help, I haven't had any problems thus far, I was just wondering as I've read that when users upgraded to 7.04 after using automatix, they found their system un-bootable. Didn't mean to cause a commotion ;) Just had some questions about things. Anyway, thanks everyone for the helpful insight. I can see that this is still a much debated topic, but am very relieved to know that I'm not one of the users experiencing problems with the program.

---

### Post by ruxbo on 2007-08-05
why is it like this in in here
a guy asked a question and it's been translated to a different way

---

### Post by MrFSL on 2007-08-05
> He was asking how to remove it (in a SUPPORT FORUM) and gave a reason for why he wanted to do such a thing. You honestly believe he has to cite reasons for his own personal decisions? He has to justify them to you?
Not at all! BUT, being a support forum, one open for public review, it is considerate and appropriate (as well as overall helpful) to not defame other people's work without siting specific issues.

 > If you actually want him to justify that personal opinion by citing it (especially considering that the main reason for this opinion was posted on Slashdot today), you are being very, very unreasonable.
Sure... cause everyone Ubuntu Forum member reads Slashdot! What was I thinking?

> asking a question about how to remove something on a technical support forum, to not only cite his reasons for wanting to remove it, but actually berating him publicly for not modifying the program which he wants to remove so that he would not be unsatisfied with it, is ridiculous.
The original post did not say, "I would like to remove automatix how do I do it?"... It said: > 've been hearing bad things about automatix as of late, and I was wondering if there is any way to undo the potential damage it has done... Furthermore, I did not berate anyone for not modifying the program... I pointed out that:
> By siting specific concerns and issues ***_users_*** can make changes/bug fixes as is the spirit of all open source software. 

> And if you do not see the reasons why this tool might be VERY DANGEROUS, I posit that you may not really know what you are talking about. Just offhand
Who is berating whom here?

> At any rate, even if none of these issues existed, and if Automatix were a perfectly safe and wonderful tool (it's not), it is still not okay to publicly berate a user asking how to remove a program on a support forum for not (a) Citing his reasons for doing so (b) Fixing the program themselves.
Again... read above I did neither of these two things.

---

### Post by ronmarley1 on 2007-08-05
Wow, another Automatix flame war.  Haven't seen one of these in a while... :shock:

---

### Post by w4ett on 2007-08-05
Yep...the original poster marked the thread "solved"...Give it up...lol

> why is it like this in in here
a guy asked a question and it's been translated to a different way

---

