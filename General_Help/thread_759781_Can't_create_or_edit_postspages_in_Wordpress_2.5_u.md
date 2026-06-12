---
title: "Can't create or edit posts/pages in Wordpress 2.5 under Ubuntu"
date: 2008-04-19
forum: General Help
---

### Post by Hedley on 2008-04-19
I upgraded my self-hosted Wordpress blog from 2.3.x to 2.5 yesterday. Prior to the upgrade, everything was fine. Now, I cannot create or edit any posts or pages. The problem appears as if it may be related to some way to the new flash function of the media uploader while operating under Linux.

When I click (for instance) "Write", the page to create a new post is displayed. Everything in the header works fine, as does everything in the right side panel. I can enter a "Title", but everything below that is inaccessible. There is a line across the bottom of the "Post" heading, but I cannot use the mouse to click into the edit box. As soon as I place my mouse anywhere below the "Post" heading, the mouse pointer changes to a "link" pointer and the following link is active:
    
        /wp-admin/media-upload.php?post_id=323&TB_iframe=true&height=500&width=640

(See screenshot [here]("http://bontano.com/169982.jpg")). 

I can use the tab key to access the edit box successfully in a post, but not a page.

I am using a Sony laptop running Ubuntu (Gutsy), and the problem occurs with both Firefox (2.0.0.13) and Opera (9.27). I am using the latest version of Adobe flash (9.0.124), I've cleared my cache, turned off all of my plugins, removed all of my widgets, and activated the Wordpress default theme, all to no avail. I also tried installing the "No Flash Uploader" plugin, which changed nothing. 

It's apparently a Linux-specific problem, as it works fine if I boot from Windows XP (tested both IE and FF). Everything was working just fine prior to my upgrade to 2.5, so I suppose something about the media uploader and/or editor is not getting along with some aspect of my Linux build (which is up-to-date). 

Anyone have any ideas?

---

