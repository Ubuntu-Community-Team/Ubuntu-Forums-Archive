---
title: "How to avoid DOCTYPE, header ..."
date: 2012-11-08
forum: General Help
---

### Post by ELMIT on 2012-11-08
I don't know how to call it, I don't know where to ask, ... please give me a hint ;-)


My problem:
I should answer with a php program JUST text
No doctype, head, body, ... just a simple text.


How to do? Where to ask?

---

### Post by Lars Noodén on 2012-11-08
If you are serving up plain text, you can set the MIME type to "plain/text"

```

<?php
header('Content-Type: text/plain');
echo ("Hello, world!");
?>

```

See the function *header()*
[http://www.php.net/manual/en/function.header.php](http://www.php.net/manual/en/function.header.php)

---

### Post by ELMIT on 2012-11-08
It did not work for me:

Now it displays:
> <!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN"
	"http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd">
<html xmlns="http://www.w3.org/1999/xhtml" xml:lang="en" lang="en">

<head>
	<title>title</title>
	<meta http-equiv="content-type" content="text/html;charset=utf-8" />
	<meta name="generator" content="Geany 0.21" />
	<link rel="stylesheet" type="text/css" href="mnp.css" />
</head>

<body>
MyText
</BODY>
</HTML>

But I need only:
MyText

---

### Post by Lars Noodén on 2012-11-09
You might double-check the actual content of the file.  It looks like the document itself is HTML.  Some of the HTML markup there implies that the page was manually written as HTML, not as some artifact of PHP.  What is the output of the file if you use a terminal window and open up the file using "cat" or "less" ?

---

### Post by ELMIT on 2012-11-09
It is a php program and it calculates some values, which I should display in PURE text.

When I just "echo $text" it looked fine, but the other machine sees all the other code, ... 
I can now make it "visible" with your methode, but I want to avoid it all together. How can I do that?

> <!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN"
	"http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd">
<html xmlns="http://www.w3.org/1999/xhtml" xml:lang="en" lang="en">

<head>
	<title>title</title>
	<meta http-equiv="content-type" content="text/html;charset=utf-8" />
	<link rel="stylesheet" type="text/css" href="mnp.css" />
</head>

<body>
Hello, world!<p>
</BODY>
</HTML>

---

### Post by ELMIT on 2012-11-09
I solved it: Just don't write the HTML tags, ... 
It was simple too easy to think of that!!!

---

### Post by Lars Noodén on 2012-11-10
> **ELMIT said:**
> I solved it: Just don't write the HTML tags, ... 
It was simple too easy to think of that!!!

Glad it's solved.  That's what I tried to express in #4 above.  It was this line which gave it away:

```

 <meta name="generator" content="Geany 0.21" />

```

Someone had used Geany to write HTML markup in the file.

---

