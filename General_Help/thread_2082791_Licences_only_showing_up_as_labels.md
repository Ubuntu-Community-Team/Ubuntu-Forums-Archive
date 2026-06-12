---
title: "Licences only showing up as labels"
date: 2012-11-10
forum: General Help
---

### Post by undeadbobop on 2012-11-10
When ever I go to view a app on any of the several software centers I try to look at the liecence because I want to know which licences it is filed under so I know what rights I have. Now all I get is a label telling me it is open source or it is propritary. But not the actual dam licence. This makes it impossible to know what I am agreeing to before I install it and it takes away the thought proccess well maybe I should see if this software abuses my basic human rights. It does not matter weather its open source or proprietary if I can not see the licence it could be abusive tors me weather it be open source or proprietary. And really those terms really should be shoved out the window because open source just means you can see the source code and that is it open source can be propratary software in the since that you are not allowed to modify it or change it. Along with that all users should have the right to know what exactly they are agreeing to before they are screwed over. I would like to know how can I view the actual licence and put the actual licence in the licence field rather than just retarded labels that have nothing to do with the licence.

Just to clairify for the 6th time:
[U][I][B]I AM NOT ASKING HOW DO I LOOK UP THE LICENSING INFORMATION FOR SOFTWARE.
I AM ASKING HOW DO I CHANGE THE FIELDS OF LICENCES IN THE UBUNTU SOFTWARE CENTER SO THEY SHOW THE ACTUAL LICENCES AND NOT GENERIC LABELS.[/B][/I][/U]

---

### Post by Lars Noodén on 2012-11-10
I just looked at Synaptic and the problem is more severe there.  It does not even have labels.  It has no licensing information at all that I can find.

---

### Post by HiImTye on 2012-11-10
you can download the package and then open it up and look for the license, it will be included with the package

---

### Post by Lars Noodén on 2012-11-10
It will be a hard bug to fix because it looks like licensing information is not contained in the package itself:
[http://manpages.ubuntu.com/manpages/precise/man5/deb-control.5.html](http://manpages.ubuntu.com/manpages/precise/man5/deb-control.5.html)
Without that, it will be very labor intensive to generate and keep up to date a database.

---

### Post by undeadbobop on 2012-11-10
> **HiImTye said:**
> you can download the package and then open it up and look for the license, it will be included with the package      No because when you download it from the software center you install it thus you already agreed to the licence not knowing what it actually you agreed to is by this point.  Meaning you could be violating it as soon as you down load it and removing it could also be against the user agreement and you would never know. if you don't care about the licence you agree to and abusive behavors you might as well be a apple fanboy mindlessly giving up all your basic human rights.

---

### Post by undeadbobop on 2012-11-10
> **Lars Noodén said:**
> I just looked at Synaptic and the problem is more severe there.  It does not even have labels.  It has no licensing information at all that I can find.
The labels do not even matter,
not knowing the licence does.

---

### Post by ajgreeny on 2012-11-10
I am fairly sure the license details of any open source application will be in the source code, not in the compiled packages that you install from synaptic or software-center.  You can, therefore, always get it if you really want it.

I'm not sure about proprietary applications; presumably you will need to accept a license at some point of the installation, so should be able to read it then.

---

### Post by undeadbobop on 2012-11-10
> **ajgreeny said:**
> I am fairly sure the license details of any open source application will be in the source code, not in the compiled packages that you install from synaptic or software-center.  You can, therefore, always get it if you really want it.

I'm not sure about proprietary applications; presumably you will need to accept a license at some point of the installation, so should be able to read it then.
why should I be digging through source code for liecences? it should inform you what the licences for the software is before you even download it. This in itself is a attack on the users. Also the label open source litterly has nothing to do with a liecence it just means you can view the source code and that is it. It is the liecence in which determines the users rights and even the source code for software can have a liecence seperate of its own. Along with that software can have multiple licences for different parts of it. Just look at windowsx/x11 , heck just look at any distrobution different parts of it will have different licences. The point being before you download and install software through the ubuntu software center you should be able to see what licences apply to the software so you can be informed of what you are agreeing to by having said software. If you don't you might aswell be a apple fanboy who just mindlessly gives up all their own rights.

---

### Post by mcduck on 2012-11-10
> **undeadbobop said:**
> If you don't you might aswell be a apple fanboy who just mindlessly gives up all their own rights.
Even though making statements like that one usually cause me to skip the thread and head on to help other people instead, I'll post you this link anyway:

[http://www.ubuntu.com/project/about-ubuntu/licensing]("http://www.ubuntu.com/project/about-ubuntu/licensing")

---

### Post by undeadbobop on 2012-11-10
> **mcduck said:**
> Even though making statements like that one usually cause me to skip the thread and head on to help other people instead, I'll post you this link anyway:

[http://www.ubuntu.com/project/about-ubuntu/licensing](http://www.ubuntu.com/project/about-ubuntu/licensing)
Yes because you know posting the licence for ubuntu has anything to do with the apps that are in the software manager.... /me facepalms massively

---

### Post by jerome1232 on 2012-11-10
> **undeadbobop said:**
> Yes because you know posting the licence for ubuntu has anything to do with the apps that are in the software manager.... /me facepalms massively at your attempts of justifying taking away the ablity to know what licence the software you are looking at to download and use.
 
Try reading the page. It tells you what the requirements are to make it into the main and restricted sections of the repositories. I also notice, that at least when I use apt-cache to look at package info, it gives me the project's homepage, so you can go to the homepage and figure out what the license is.

---

### Post by undeadbobop on 2012-11-11
> **jerome1232 said:**
> Try reading the page. It tells you what the requirements are to make it into the main and restricted sections of the repositories. I also notice, that at least when I use apt-cache to look at package info, it gives me the project's homepage, so you can go to the homepage and figure out what the license is.
Try reading the thread to begin with. All I am asking for is something they once had and HOW to do it. Not some cryptive way for me to look for the dam licences every time and the fact they just label all licences as open source and proprietary instead of the actual licence is dumb to begin with and entirely pointless and all I want is to change the labels back to the actual licences and I am asking HOW not looking it up and doing research every time and clearly the fact you are defending this way is showing me that non of you care what you agree too.

The label's open source and propratary should not be there to begin with, but more or less since no one is actually reading I am asking HOW do I get it so the licences field actually shows the actual licences instead of retarded dumb down labels.

---

### Post by jerome1232 on 2012-11-11
Good luck getting any help with that attitude, we are all volunteers here and don't appreciate that kind of talk.

I apologize for donating a portion of my time to helping you figure out a way to find the license information, I won't repeat the mistake.

---

### Post by undeadbobop on 2012-11-11
> **jerome1232 said:**
> Good luck getting any help with that attitude, we are all volunteers here and don't appreciate that kind of talk.

I apologize for donating a portion of my time to helping you figure out a way to find the license information, I won't repeat the mistake.
Every forum is volunteer based...... I don't appreciate being constantly insulted and counter productive posts after counter productive posts made by people who clearly do not care about the subject matter to actually read what the person is asking for. More or less you only came here to act high and mighty and start flame wars other wise you would have actually read the thread, and you would have noticed I already clarified that is not what I am looking for. No instead you came to offer input that has nothing to do with what I am asking and you  acting like your time is more valuable than everyone else's.

Good luck "donating a portion of your time to helping" 
Don't see how you can do that since you don't bother to read the thread you are responding to.

---

### Post by undeadbobop on 2012-11-11
> **Lars Noodén said:**
> It will be a hard bug to fix because it looks like licensing information is not contained in the package itself:
[http://manpages.ubuntu.com/manpages/precise/man5/deb-control.5.html](http://manpages.ubuntu.com/manpages/precise/man5/deb-control.5.html)
Without that, it will be very labor intensive to generate and keep up to date a database.
sorry about before...

I thought thought that the labels where a result of a query not what is actually stored in the database. So another query is my solution I thought. But more or less I am asking how because I do not understand their database systems and I can't even see it. It is more or less dealing with their repository sources data base. But I noticed there was nothing there about how the licence field is stored in that link....

---

