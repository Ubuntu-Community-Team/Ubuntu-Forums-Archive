---
title: "Connection to Ubuntu forums not secure"
date: 2023-04-01
forum: General Help
---

### Post by kabirgandhiok on 2023-04-01
Hi, there have been duplicate posts like this one, but the ones I came across were all closed without a definitive solution or response.

On Firefox the security padlock has that warning sign in it while browsing the Ubuntu forums and clicking it says connection not secure and that parts of the website are not secure such as images.
Is this a concern? Is it something that needs to be fixed?

The security warning is only present while browsing through forum sections and posts but not while creating a post.


[https://ubuntuforums.org/attachment.php?attachmentid=291999&stc=1](https://ubuntuforums.org/attachment.php?attachmentid=291999&stc=1)

---

### Post by TheFu on 2023-04-01
Do your own research to understand the nature of the warning and what it really means. Then you'll make informed choices.
[https://www.cloudflare.com/learning/ssl/why-use-https/](https://www.cloudflare.com/learning/ssl/why-use-https/) says why HTTPS could be important.  

I'm not worried about it, but my browser doesn't complain and when I look at the security information for this page, none of the content is using HTTP.

---

### Post by kabirgandhiok on 2023-04-01
> **TheFu said:**
> I'm not worried about it, but my browser doesn't complain and when I look at the security information for this page, none of the content is using HTTP.

This page does not give me any warning either. But within General Help where all the threads are listed that's where I see these warnings if I click the padlock in the browser. Again, I don't see them inside individual posts or while replying to posts but only on the pages where all threads are listed. Is this the case for you as well? I did try to figure out the reason but so far couldn't find much, will continue. All other websites are secured with https on the browser.
Thanks for taking the time.

Edit: According to mozilla support a padlock with a triangle in it indicates passive insecure content such as images. Be default Firefox does not block mixed passive content and it simply shows a warning that the page isn't fully secure.

---

### Post by kabirgandhiok on 2023-04-01
setting value of <security.mixed_content.upgrade_display_content = true> from within Firefox config fixes this.
marking solved.

---

### Post by TheFu on 2023-04-01
> **kabirgandhiok said:**
> setting value of <security.mixed_content.upgrade_display_content = true> from within Firefox config fixes this.
marking solved.

I check the media tab and is says all the media provided is using https, but I don't allow bookface or much of google any access to the network, so their ad networks can't do non-secure junk.

---

### Post by kabirgandhiok on 2023-04-01
> **TheFu said:**
> I check the media tab and is says all the media provided is using https, but I don't allow bookface or much of google any access to the network, so their ad networks can't do non-secure junk.
Thanks for that, I can see google-anal ytics trackers inside the tracking content tab, fortunately it is being blocked. :)

---

