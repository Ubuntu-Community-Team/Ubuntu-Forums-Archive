---
title: "Help needed on updating Hardy Heron's files"
date: 2008-05-18
forum: General Help
---

### Post by newbiehardy on 2008-05-18
Hi Ubuntu gurus,

This is my first experience with Hardy Heron.

When trying to download the media codecs as stated in the article "[Top 10 Things That You Need to Do After Installing Hardy Heron]("http://maketecheasier.com/10-things-you-need-to-do-in-hardy-heron/2008/05/15")", most of the codecs loaded uneventfully.

But when it came to downloading the macromedia files, the download just stalled at around 300K and it remained that way for more than 10 minutes.

I got frustrated and closed the terminal window.

That was a big mistake.

Now when I click on Synaptic Package Manager, the latter wouldnt run at all.

The error message is : "
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report."

So I went into terminal mode and typed in "dpkg --configure -a" (without the quotes), but got another error message instead

"dpkg: requested operation requires superuser privilege"

Being the only user in this freshly installed system, am I not the superuser?

What am I doing wrong and what can I do to solve it?

Thanks in advance for good advice.

James the frustrated.

---

### Post by pcadotte on 2008-05-18
Hi

superuser is different from your normal daily usage id.

try:
```
sudo dpkg --configure -a
```

---

