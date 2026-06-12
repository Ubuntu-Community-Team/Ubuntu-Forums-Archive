---
title: "how to integrate a custom facebook stream into wordpress ?"
date: 2015-02-23
forum: General Help
---

### Post by dilbert_one on 2015-02-23
hello dear ubuntu-experts, 


today i have a php or better said - a wordpress-related question....


i want to run and show facebook-actiity feeds (in other words "streams of two different facebook sites) 

that said i cannot do this with one plugin - can i? 

well some guys taled bout a solution of copying and cloing a wordpress plugin 

I want to have multiple instances of the plugin running so i can have different related content on a single page. that said i heard that some guys just do one thing; they coly the copy the plugin.


[https://wordpress.org/support/topic/installing-2-copies-of-the-same-plugin?replies=8](https://wordpress.org/support/topic/installing-2-copies-of-the-same-plugin?replies=8)


but thie does not work - so i have to do one facebook-feed with a version like so 

question - how to include the code:

[https://developers.facebook.com/docs/plugins/activity](https://developers.facebook.com/docs/plugins/activity)

Initialize the JavaScript SDK using this app: booksocial123

  Include the JavaScript SDK on your page once, ideally right after the opening <body> tag. 
 
```
 

<div id="fb-root"></div>
<script>(function(d, s, id) {
  var js, fjs = d.getElementsByTagName(s)[0];
  if (d.getElementById(id)) return;
  js = d.createElement(s); js.id = id;
  js.src = "//connect.facebook.net/en_GB/sdk.js#xfbml=1&appId=473241986032774&version=v2.0";
  fjs.parentNode.insertBefore(js, fjs);
}(document, 'script', 'facebook-jssdk'));</script>


```

or see here....:
Place the code for your plugin wherever you want the plugin to appear on your page.

```
<div class="fb-activity" data-site="facebook.com/literaturen" data-action="likes, recommends" data-width="350px" data-height="350px" data-colorscheme="light" data-header="true"></div>

```


love to hear from you 

regards

---

### Post by tgalati4 on 2015-02-24
I think the big problem is that you have to authenicate the connection with facebook.  That creates a key tied to your IP address to allow the activity stream to be pushed to your computer.  Simply using the plug-in twice means you have two different authentication keys for the same IP, and that probably fails.

What you could do is create a dummy page with one facebook feed on a different machine with a different IP (possibly through a virtual machine), then write a script to scrape that page using CURL to display that feed on your wordpress page and use the facebook plug-in for the other.  I would ask on both the wordpress and facebook forums.  I'm sure you are not the only one that wants to display two feeds at once.

---

### Post by dilbert_one on 2015-02-24
Hello dear tgalait4 

many many thanks for the answer - i gueess that you hit the point 100 % 

> **tgalati4 said:**
> I think the big problem is that you have to authenicate the connection with facebook.  That creates a key tied to your IP address to allow the activity stream to be pushed to your computer.  Simply using the plug-in twice means you have two different authentication keys for the same IP, and that probably fails.

What you could do is create a dummy page with one facebook feed on a different machine with a different IP (possibly through a virtual machine), then write a script to scrape that page using CURL to display that feed on your wordpress page and use the facebook plug-in for the other.  I would ask on both the wordpress and facebook forums.  I'm sure you are not the only one that wants to display two feeds at once.


guess that you are pointing out the issues i have...




i have investigated some things... just some basics on facebook-pages: how to do this test page... 

note: i run  a wordpress with several plugings such as 

Feed them social -plugin 
[http://www.slickremix.com/support-fo...em-social-2/1/]("http://www.slickremix.com/support-forum/forum/feed-them-social-2/1/")
[https://wordpress.org/plugins/feed-them-social/](https://wordpress.org/plugins/feed-them-social/)

this plugin generates the so called shortcode for displaying feeds in a widget.


but i have some issuues: 

note i an create  a feed from the follwing 

[fts facebook id=Literaturen posts_displayed=page_only type=page]
[fts facebook id=Literaturen posts_displayed=page_only type=page]

THIS IS DERIVED FFOM MY facebook-page; 

[https://www.facebook.com/literaturen](https://www.facebook.com/literaturen) 

so  far so good: 

now - i want to  try out how to add a second feed for this wordpress-plugin feed-them-social 

see the feed-idea: 

i want to create a feed from [https://www.facebook/foo](https://www.facebook/foo)
i want to create a feed from [https://www.facebook/bar](https://www.facebook/bar) 



how to do that? 

we see a test page: 

how to generate some facebook-feed from this page 

[https://www.facebook.com/pages/Test-Page/301396262700](https://www.facebook.com/pages/Test-Page/301396262700)

[fts facebook id=Test-Page posts_displayed=page_only type=page]

Error: (#803) Some of the aliases you requested do not exist: Test-Page
Type: OAuthException
Code: 803


[fts facebook id=Test-Page/301396262700 posts_displayed=page_only type=page]

Error: Unknown path components: /301396262700/posts
Type: OAuthException
Code: 2500

why do i get these errors 

can you provide some demos or default-types of feed-displays of facebook 

is this possible?

---

### Post by Bucky Ball on 2015-02-24
*Thread moved to **General Help**.*

The Cafe is not a support area.

---

### Post by tgalati4 on 2015-02-24
I'm not a frequent facebook user, but perhaps there is a way to get two feeds on one facebook page, then stream that to wordpress.  Perhaps there is a facebook plug-in that integrates two streams into one.

Ask the folks in the slickremix plug-in forum:  [http://www.slickremix.com/support-forum/forum/feed-them-social-2/1/](http://www.slickremix.com/support-forum/forum/feed-them-social-2/1/)

Other folks are having issues with authentication.  Some are due to changes to the facebook API, which is always a risk when you rely on another service.  Sometimes that service goes away.

You can use the "feed-them-social" plug-in to integrate several different social feeds, but it does not appear to support two different feeds from the same service.  That is a Use Case that was not considered when it was written.

---

### Post by dilbert_one on 2015-02-25
hello many thanks for the answer. i will figure it out and  come back and report. 

untill later

---

