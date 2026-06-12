---
title: "What the crap? Can't figure out RSS."
date: 2008-02-13
forum: General Help
---

### Post by SZF2001 on 2008-02-13
Alright. I've followed tutorials and know the bare bone minimum of an RSS feed by saving with a .xml file and all that fun stuff. I'm trying to made a podcast for a group in school and this RSS stuff seems like the easiest way.

Anyway, here's a sample of what I've made for an example. Please point out my flaws.

```
<?xml version="1.0" ?>
<rss version="2.0">
	<channel>
		<title>Announcements</title>
		<description>Updated daily announcements for the school.</description>
		<link>http://www.crap.com</link>
		
		<item>
		<title>Stuff Happens Again</title>
		<description>Yea. Here's some stuff. It's the announcements.</description>
		<link>http://www.crap.com/announcements2.html</link>
	</item>
	<item>
		<title>Stuff Happens</title>
		<description>This is the first page. The update should be above.</description>
		<link>http://www.crap.com/announcements1.html</link>
	</item>
</channel>
</rss>
```

And here's another thing - I've noticed the RSS icons popping up in browsers (in Firefox specifically they sho up in the URL bar), and when I click them it takes me to this little layout page of whats new. For an example you can even use Ben's homepage, click the RSS icon, and be taken to this layout page.

But mine just don't do that. Why? Every time I see the .xml file in my browser, it just shows the code - with this code I know I've done it correctly (as my stuborness points out) but it just won't show a layout.

I'm new to all this. As long as an app like GPodder or iTunes has the .xml file, that should be fine, right? It'd still be nice to make or have a layout. Is it css?

---

### Post by schaumkeks on 2008-02-13
The RSS icons are shown in the URL bar if you embed a link into your webpage like this:
```
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd">
<html xmlns="http://www.w3.org/1999/xhtml">
<head>
  <meta content="text/html; charset=UTF-8"
 http-equiv="content-type" />
  <title>Content Title</title>
<link rel="alternate" type="application/rss+xml"
   title="RSS" href="feed.rss" />
</head>
<body>
Content
</body>
</html>
```

You just have to change the href of the link tag to point to the correct location of your rss feed file.

The feed code is ok, you can check it with the [W3 Feed Validator]("http://validator.w3.org/feed/#validate_by_input")

What browser are you using? I tried opening the feed directly or via feed icon and Firefox shows as expected the feed content and the possibility to subscribe with nice layout.

Bye, Sven

---

### Post by SZF2001 on 2008-02-13
I'm using Ubuntu's updated Firefox (not 3).

I guess the feed seems valid, I'll try adding that icon real quick and post the results.

---

