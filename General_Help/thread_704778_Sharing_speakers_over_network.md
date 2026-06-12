---
title: "Sharing speakers over network?"
date: 2008-02-22
forum: General Help
---

### Post by AlbinoClock on 2008-02-22
I have an XP machine and an Ubuntu machine networked together. I want to use the speakers on the XP machine for both computers. I downloaded PulseAudio for Windows and Ubuntu, but the Windows version doesn't work. 

Are there any alternative ways to do this?

---

### Post by UK-Wobbie on 2008-02-22
> **AlbinoClock said:**
> I have an XP machine and an Ubuntu machine networked together. I want to use the speakers on the XP machine for both computers. I downloaded PulseAudio for Windows and Ubuntu, but the Windows version doesn't work. 

Are there any alternative ways to do this?

What i did on my two computers on one speakers :)
Is to get two big head phone music cables what plugs into your sound card, Then a two way cable output what yets you plug into your speakers.

So you got two sound cables going from the two computers into a two way output.
It works OK :lolflag:

But is your computers in the same room?
Saying it's on a network, Or are they not in the same room? :)

---

### Post by AlbinoClock on 2008-02-22
> **UK-Wobbie said:**
> What i did on my two computers on one speakers :)
Is to get two big head phone music cables what plugs into your sound card, Then a two way cable output what yets you plug into your speakers.

So you got two sound cables going from the two computers into a two way output.
It works OK :lolflag:

But is your computers in the same room?
Saying it's on a network, Or are they not in the same room? :)

They're right next to one another, using one keyboard and mouse with Synergy. Unfortunately the sound card on my linux machine seems to be bad (the computer was a ground-score), so I think I'm limited to network-based software options.

---

### Post by Whiffle on 2008-02-22
> **UK-Wobbie said:**
> What i did on my two computers on one speakers :)
Is to get two big head phone music cables what plugs into your sound card, Then a two way cable output what yets you plug into your speakers.

So you got two sound cables going from the two computers into a two way output.
It works OK :lolflag:

But is your computers in the same room?
Saying it's on a network, Or are they not in the same room? :)


Actually thats not a good way to do it.  If they play at the same time one is more or less pushing its audio signal back into the other one.  A proper setup would have a summing amplifier in the middle, aka a mixer.

My 12 year old speakers have two inputs :-P

As far as networked sound, if the computers aren't far apart you could run the output of one computer into the line-in input of the other one, and hook the speakers to that one.  Then just unmute the line in and it should be good to go.  Thats the way I used 2 sound cards on mine for a while.

---

### Post by UK-Wobbie on 2008-02-22
> **AlbinoClock said:**
> They're right next to one another, using one keyboard and mouse with Synergy. Unfortunately the sound card on my linux machine seems to be bad (the computer was a ground-score), so I think I'm limited to network-based software options.

Have a look at this
Share speakers between two different computers
[http://articles.techrepublic.com.com/5100-1035_11-5238134.html](http://articles.techrepublic.com.com/5100-1035_11-5238134.html)

On the site you can see what i was on about with the cables and outputs
[IMG]http://techrepublic.com.com/i/tr/cms/contentPics/share-speakers-5238134A.jpg[/IMG]

You got the 2 input phone cables and the one 2 way output box thing :lolflag:

It's like what i was saying i got a linux computer next to my XP computer to,
And i got the same speakers linked up to the two computers.

But with you network may be best if your sound card is bad. :)

---

### Post by UK-Wobbie on 2008-02-22
> **Whiffle said:**
> Actually thats not a good way to do it.  If they play at the same time one is more or less pushing its audio signal back into the other one.  A proper setup would have a summing amplifier in the middle, aka a mixer.

My 12 year old speakers have two inputs :-P

As far as networked sound, if the computers aren't far apart you could run the output of one computer into the line-in input of the other one, and hook the speakers to that one.  Then just unmute the line in and it should be good to go.  Thats the way I used 2 sound cards on mine for a while.

Not if you playing on one computer at a time :)

Saying all that, If you have got one Dell or what make monitors! And they have got two monitor cable inputs, And you got your two computers plugged up to the one monitor.
It's not like you be using the two computers at the same time?
As i got two Dell monitors and one keyboard and mouse all plugged up to the two computers.
And sound coming from the same speakers lol :)

---

### Post by UK-Wobbie on 2008-02-22
> **Whiffle said:**
> Actually thats not a good way to do it.  If they play at the same time one is more or less pushing its audio signal back into the other one.  A proper setup would have a summing amplifier in the middle, aka a mixer.

My 12 year old speakers have two inputs :-P

As far as networked sound, if the computers aren't far apart you could run the output of one computer into the line-in input of the other one, and hook the speakers to that one.  Then just unmute the line in and it should be good to go.  Thats the way I used 2 sound cards on mine for a while.

If you played music in your line-in input Windows will not like it.
And it's more bad then anything lol, Thats going to push sound from one sound card in to a other sound card and the computer will be turned off,
So thats a bad thing to do.

---

### Post by Whiffle on 2008-02-22
Well, considering that an input is designed to have an audio signal inputted.  It doesn't matter if its on or off, its designed to take input.  Daisy chaining them like that is fine.  I never had a problem with windows and inputs...

On the other hand, combing the two signals with a simple splitter like that introduces issues since there is no isolation between the two different sources.  Heck, there is a reason they put multiple inputs on things and a reason they invented things like the op-amp summer, to combine signals!

I could go into the theory and the math, but its friday night, and I don't feel like digging out my circuits book.  If you read the comments in that link you posted, there are several who have the same issues with this that I do.  Its not a sound way to do it.

Computer monitors aren't even related to this.  My dell monitor has a switch built into it, you couldn't display more than one picture if you wanted to.  Totally different than audio.

As far as the OP's issue, I think the only real solution for you is that Pulseaudio thing,  I didn't find much on google.  Or just buy another sound card (mine was $12!! after rebates...)

---

### Post by AlbinoClock on 2008-02-22
> **Whiffle said:**
> Well, considering that an input is designed to have an audio signal inputted.  It doesn't matter if its on or off, its designed to take input.  Daisy chaining them like that is fine.  I never had a problem with windows and inputs...

On the other hand, combing the two signals with a simple splitter like that introduces issues since there is no isolation between the two different sources.  Heck, there is a reason they put multiple inputs on things and a reason they invented things like the op-amp summer, to combine signals!

I could go into the theory and the math, but its friday night, and I don't feel like digging out my circuits book.  If you read the comments in that link you posted, there are several who have the same issues with this that I do.  Its not a sound way to do it.


As far as the OP's issue, I think the only real solution for you is that Pulseaudio thing,  I didn't find much on google.  Or just buy another sound card (mine was $12!! after rebates...)

If I could just get PulseAudio to work for Windows, I'd be out of the woods. Has anyone else had experience with this program in XP?

---

### Post by AlbinoClock on 2008-02-23
Other suggestions?

---

