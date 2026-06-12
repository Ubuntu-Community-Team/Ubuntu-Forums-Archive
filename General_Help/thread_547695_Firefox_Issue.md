---
title: "Firefox Issue"
date: 2007-09-10
forum: General Help
---

### Post by Bofur on 2007-09-10
I'm taking an Astronomy class and my professor posts embeds his slides into a web page. Anyways, when I try to view it using Firefox, it won't work. The only known way you can view it that I know of is to use IE. I was just wondering if there was a workaround for this? Heres the link so you guys can see for yourself.

[http://physics.uwyo.edu/~mpierce/A1050/2007_08_27w_files/error.htm](http://physics.uwyo.edu/~mpierce/A1050/2007_08_27w_files/error.htm)

Thanks for any help in advance. :popcorn:

---

### Post by reckless2k2 on 2007-09-10
int he community documents there is a spec on how to handle this with a plugin. i think it's mplayer-plugin. i'm not sure. look in the community docs. or query view embedded video in firefox. it's not hard to do at all. the only hangup is if an IE specific site runs using activeX. then you won't be able to do it in linux. they say you can with wine but it doesn't work so well.

---

### Post by p_quarles on 2007-09-10
I looks like that site does indeed use ActiveX. Overall, I would say that it's in the running for the most poorly-designed web site on the internet. The course's front page nearly blinded me. 

Basically, this idiot should get a student assistant who knows web standards basics. Failing that, he should be prohibited from requiring students to use his web page.

I mean, the link to the course syllabus opens a .doc file! **** ain't right.

---

### Post by Bofur on 2007-09-10
Is there a reason Firefox doesn't use ActiveX? And is there a plugin or something I can install?

---

### Post by Maestro23 on 2007-09-10
> **Bofur said:**
> Is there a reason Firefox doesn't use ActiveX? And is there a plugin or something I can install?

Linux and Active X do not play well with each other.  I don't know what version of IE that site requires you to use, but I did some Googling and found a possible work-around for you.  

[http://www.tatanka.com.br/ies4linux/page/Main_Page](http://www.tatanka.com.br/ies4linux/page/Main_Page)

*If you really need that site, you can also try installing WINE and running IE through it.

WineHQ: [http://www.winehq.org/](http://www.winehq.org/)

Like the earlier guy posted, that is just bad site design anyway.  Good luck man.

---

### Post by Steveway on 2007-09-10
ActiveX is a major security risc.
It allows to run any app on your PC.
It's not worth the effort  anyone put in.
Just tell him he is an ID 10 t or better look for someone that has any knowledge in the w3c-standards and let him code for your prof.
That page is made of evil and fail.

---

### Post by p_quarles on 2007-09-10
> **Bofur said:**
> Is there a reason Firefox doesn't use ActiveX? And is there a plugin or something I can install?
Yes. It's a proprietary protocol owned by Microsoft. Short of reverse engineering it, there's no way to get it to work with non-MS software. There is no plugin.

Using Wine to install MSIE is the only option for Linux. Probably a lot easier to go to a computer lab and watch the presentation there.

---

### Post by reckless2k2 on 2007-09-10
i have that ie4linux installed just for activex forced sites and it is just buggy. it was easyt o setup but is just not worth it. go to the pc lab like the other post suggested. hahaha

---

