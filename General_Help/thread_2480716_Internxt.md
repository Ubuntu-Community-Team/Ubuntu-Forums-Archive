---
title: "Internxt?????"
date: 2022-11-07
forum: General Help
---

### Post by richramik on 2022-11-07
Hey Gang:

Has anyone had experience with INTERNXT?????  I need to use this on Ubuntu 22.04, Windows 11, and Andriod Galaxy S21.

I am moving away from dropbox.

Thanks,
Rich Ramik

---

### Post by DuckHook on 2022-11-08
I have no experience with Internxt, so I cannot answer your question directly.

But if you are moving away from Dropbox due to privacy concerns, then consider the following.

Caveat: What follows is my highly subjective personal opinion. You will get opposing answers from other more knowledgeable people, so please do your own research before going by what I say.
[B]
I don't trust any third party "cloud" solution:[/B]

[LIST]
[*]I have no way of auditing their actual practices, so all the pronouncements in the world stating how much they "respect my privacy" is—as far as I'm concerned—self&#8209;serving marketing&#8209;speak.
[*]Not a week goes by that I don't receive a warning from my security feeds that some cloud provider has been compromised and thousands or even millions of their customer accounts exposed.
[*]If I don't have complete control of the cloud infrastructure, then it's not my cloud, nor is it my data. At most, I get the false *illusion* that it's my data, and this is a dangerous misconception.
[/LIST]
Notwithstanding my concerns, clouds are extremely useful, so when I thought I had no other choice, I did use third&#8209;party cloud services. But the residual issues at the back of my mind always bothered me to no end.

Examples:

[LIST]
[*]I transferred all of my cloud photos from Google to Piwigo (another 3rd party cloud solutions) about three years ago. But what assurance do I have that Google actually deleted my photos and they aren't still floating around in Google's servers (only no longer accessible to me)?
[*]Recently, I didn't renew my Piwigo account either. Again, what verifiable assurance do I have that they will be as good as their word and completely delete my photos?
[*]What is my recourse if some scumbag penetrates these cloud providers' defences (as noted, a well&#8209;nigh weekly occurrence) and steals (and/or scrambles) my data?
[/LIST]
My solution:

For about two years now, I've been hosting my own cloud using Nextcloud. I couldn't be happier.

**Pros:**

[LIST=1]
[*]It's FOSS. That means free: financially, philosophically and in terms of data sovereignty.
[*]It has clients for all OSes: Linux, Windows, Mac, iOS and Android.
[*]It's absolutely all under my control. I have no concern about my important data being exploited by outsiders for nefarious purposes.
[*]No built in storage limits. Storage is only limited by the size of the HDD I decide to use.
[*]The additional capabilities are just as awesome—my contacts and calendars are all on Nextcloud too (which I didn't bargain for when first installing it). Mrs DH is playing with the NC recipe app. The map app is really cool. I haven't tried the video conferencing app yet, but it's there, so no more data slurping by Zoom or MS either.
[*]If initially set up properly, cloning all data to a remote location (for redundancy) is easy.
[/LIST]
**Cons:**

[LIST=1]
[*]Requires appreciable infrastructure investment, not only in HW but also in a robust, reliable and high bandwidth Internet connection. Some people report success running NC on a RPi; I wouldn't recommend it. I use a static IP address, but others have successfully used a DDNS solution.
[*]You are your own sysadmin. Although NC is relatively easy to administer for those with some IT experience, it is a serious implementation and not for dilettantes.
[*]For SOHO users, it's a single point of failure. Unlike the giant cloud providers (in which redundancy is a given), if your NC server goes down, so does your functionality. Redundancy is possible, but it requires more HW and an involved implementation that's not for the fainthearted.
[*]You are solely responsible for your own backups, security, etc. This is not that hard, but it's an important consideration.
[/LIST]
If interested, a web&#8209;search will return many tutorials explaining how to install and run it. NC server is available as a snap in Ubuntu, but I would recommend what I consider to be a *proper* install from Nextcloud itself:  [https://nextcloud.com/](https://nextcloud.com/)

---

### Post by richramik on 2022-11-09
That is quite a bit of information you provided.  I really appreciate it.

What I am trying to accomplish is simple. I have a handful of files (calc spreadsheets) that started life on my Ubuntu 22.04 system at home.  I need, occasionally, to have access to one or possibly two files on the Android (Galaxy S21) mobile phone.  I also need the same on my computer at work: Windows 11.  I have a total of 25 small calc sheets.

I don't mind learning new things, but what I do is more related to convenience rather than necessity, i.e., medication list, model train data (hobby), DCC (Digital Command Control) information also related to model trains, and the like.  I don't share the information nor collaborate with other folks.  

Now you have an idea on what I am really doing.  I realize now that I should have stated this up front.

Thanks,
Rich Ramik

---

### Post by DuckHook on 2022-11-09
Ah, okay.

So, given your use case, my solution is a bit like killing a fly with a cannon.

If the data you intend to leave floating out there is not sensitive and Nextcloud's other offerings do not interest you, then I understand why NC is not appropriate.

But if this is the state of your needs, then why are you moving away from Dropbox? Such limited usage would presumably qualify under their 2 GB free account and they are a proven entity with access all over the world, so why switch?

As mentioned, I don't know anything about Internxt, but I do use a third&#8209;party cloud service for files that are completely insensitive and that I couldn't care less if I were to lose. I should add that not many files meet that criteria, so it's a service I rarely use.

[https://disroot.org/en](https://disroot.org/en)

Disroot is run by a small collective of idealistic IT gurus who have set up shop in Amsterdam. It is committed to offering a small, anti&#8209;corporate, decentralized and federated suite of goods that champions philosophical freedom and privacy over money making (or, at least, that is what *their* marketing material says). They survive through donations and a traditional income model that charges real money for storage over 2 GB. This is an income model that does not rely on data slurping, so it gives credence to their privacy claims. Further credibility can be found in the fact that, if you lose your password, they cannot recover your account. Everything is encrypted and they have no "master" password or key, so if you forget your password, it's game over.

If you can overlook their rather anarchistic and save&#8209;the&#8209;earth vibe, they are something to consider. I've used them now for two years with no complaints. They are dependable enough for a boutique operation that runs out of one city and is therefore subject to a single point of failure; unlike Dropbox, which has distributed servers all over the planet.

Interesting to note that Disroot runs Nextcloud, so, essentially, you would be using NC through a third&#8209;party provider. This gives you the benefit of their other bells and whistles too. They have everything from temporary bin buckets to chat to collaborative office suites, but their most useful feature for me is their accompanying e-mail account (which counts as part of their 2 GB data limit). Not bad for a service that is absolutely free (as in both beer *and* speech).

Accessing your files would not be a problem on any platform. You would need the Nextcloud app on your Android phone, but that's easy. The Disroot storage can be set up as a Nautilus folder on Ubuntu, so that is also easy. The only thing I'm not sure of is Windows, since I don't use that. But it's not hard to fire up a web browser to access the files through the Disroot site, so that shouldn't be a concern either.

I obviously trust them enough to use them, but you would need to do your own research to satisfy yourself that they are dependable and trustworthy.

---

### Post by richramik on 2022-11-10
Thanks again.  I will look into disroot.  Sounds interesting and it just maybe the solution I have been looking for.

Keep on ducking and quacking!!!!!!

Rich Ramik

---

