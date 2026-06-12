---
title: "My Ubuntu keeps breaking on every update :("
date: 2015-09-02
forum: General Help
---

### Post by berry-jordaan on 2015-09-02
Hello form windows land.
I have a Lenovo Y510P and I love it.... when it's running Windows 8.1.

I don't think it's Ubuntu's fault as much as the Kernels and drivers not keeping in sync.

I exclusively use Ubuntu at work (Dell machine) and many things is just easier to do in Linux so I don't want give that up. In the last 5 months, I had to reinstall my Ubuntu four times! Every time I have to jump through different hoops in order to get my OS working again and it ussaly ends up in me reinstalling my OS. My time is extremely limited and I don't have time to continuously debug my Ubuntu after every update. 

If the issues I had could be solved in the OS that would have been OK but every time it's Ubuntu booting to a black screen. I can't debug or request for help if I can't get into my OS. I can access the command line.

I was a fan of Mint for a while but Mint has also been troublesome for me.

So here is my problem: My laptop keeps booting to a black screen with only the cursor flashing.

If you have na Ideapad Y510P, how do you solve these issues?

---

### Post by QIII on 2015-09-02
Hello!

Would you please provide the hardware specifications of your machine?  Simply supplying a model number presumes you expect others to look it up.

Your description of your issues is very generalized and vague.  The more detail you can provide, the more likely you are to get an answer.

The black screen could be a video driver issue.  What driver are you using and how did you install it?  This sort of thing happens after updates if a proprietary driver is  installed from outside the Canonical repo.

---

### Post by howefield on 2015-09-02
> **berry-jordaan said:**
> So here is my problem: My laptop keeps booting to a black screen with only the cursor flashing.

The machine looks like it has an nvidia card ?

I don't have that machine, but could be a kernel update breaking the drivers. You could try removing the proprietary drivers before upgrading assuming that you do use them, then put them back once the machine has been updated and rebooted.

Does your machine currently boot to a black screen or are you describing what happens on update ?

---

### Post by Yellow Pasque on 2015-09-02
So does it break on literally every update, or just on kernel updates?

> **QIII said:**
> Simply supplying a model number presumes you expect others to look it up.

LOL, I feel very lucky when the OP gives a model number. I imagine some of these people that don't even give the model number trying to make an appointment with their mechanic as something like:

Motorist: My engine isn't running right.
Mechanic: What kind of car and engine do you have?
Motorist: It's a Ford.
<awkward silence, Mechanic facepalms>

---

### Post by monkeybrain20122 on 2015-09-02
Also Ubuntu version and if it is a Nvidia card which driver. I think there is a bug in 14.04 and one Nvidia driver so that it breaks when kernel updates. The fix would be to switch to a different driver (like 331 to 341 or something like that,--the numbers are made up so don't try that.--these version numbers confuse me)

---

### Post by berry-jordaan on 2015-09-03
Sorry for being vague on the details but my hope was that if I give a model number, someone with a similar model would be able to give me some advice. What usually happens is good folk try to help but sends me on a wild-goose chase. I'm not ungrateful but every few months it's the same thing :( Sorry.

I had the standard Ubuntu recommended, Nvidia drivers but it went black screen on me last week after an update. I also tried the latest Nvidia drivers but got the exact same problem. 

I'm currently on version 14.04. However, the black screen after random updates has been happening for the last few Ubuntu releases. I'm sure it's a kernel issue but it's getting annoying.
I reinstall Ubuntu every few months because of updates breaking my machine. I didn't need to reinstall Windows for over 2 years now (even after upgrades) which is not cool. Before Unity, Ubuntu used to be solid and reliable.

I should not blame Ubuntu though. It's must be my specific hardware combination but man, it's getting predictable. Ubuntu begs me to update and when I do, my machine don't boot up. Yawn.

> **Temüjin said:**
>  LOL, I feel very lucky when the OP gives a model number. I imagine some of these people that don't even give the model number trying to make an appointment with their mechanic as something like:

Motorist: My engine isn't running right.
Mechanic: What kind of car and engine do you have?
Motorist: It's a Ford.
<awkward silence, Mechanic facepalms>

I must admit that I don't get your reference. I take my car to a specialized mechanic. I give them my car model and the year it was released and they know exactly what my car is composed of. I don't need to know anything about what's going on under the hood. 

But then again, I have never owned a Ford before :)

> **Temüjin said:**
>  So does it break on literally every update, or just on kernel updates?

I must admit that I'm being overly dramatic. It doesn't break on every update. However, it's been breaking often enough for me to avoid updating so naturally when I do decide to naively trust an update request, it breaks. From my perspective, it feels like every update breaks my machine but that's not the truth.

> **howefield said:**
>  Does your machine currently boot to a black screen or are you describing what happens on update ?

My machine currently boot to a black screen with a white flashing cursor. This is slightly different than other issues I have had in the past which includes Ubuntu booting to a black screen with no cursor, or booting to a kernel panic error, or freezing on boot with no keyboard input.

Other errors involves some grub errors. (Sorry can't remember the error but I were able to get back from that one without a reinstall)

---

### Post by Yellow Pasque on 2015-09-03
> **berry-jordaan said:**
> I must admit that I don't get your reference. I take my car to a specialized mechanic.
I was talking (to QIII) about people who don't give their model number or any details about their system. Nevermind...

> I must admit that I'm being overly dramatic. It doesn't break on every update.

Okay, so does it break only on kernel updates? If so, I would suspect proprietary nvidia video driver. You may want to tell us if you install the nvidia driver and how you do so.

---

### Post by berry-jordaan on 2015-09-04
> **Temüjin said:**
> I was talking (to QIII) about people who don't give their model number or any details about their system. Nevermind...

I guess I was so anxious to slip a Ford joke in there that I didn't take in the entire comment. Sorry :)

I don't know what the version is but I installed it by using the "Additional Drivers" app. I selected the [Recommended] option.

---

