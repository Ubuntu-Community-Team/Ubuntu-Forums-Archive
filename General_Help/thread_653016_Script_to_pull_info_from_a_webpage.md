---
title: "Script to pull info from a webpage"
date: 2007-12-29
forum: General Help
---

### Post by ~LoKe on 2007-12-29
There's a website ([here](http://et.splatterladder.com/?mod=serverinfo&idx=311229&section=ranking)) which has ranking information.  I'd like to write a script, the language doesn't matter, that I can execute via the terminal that will pull the rank, name and rating for a player.  (+Recoil).  I realize the name uses color tags, so if that makes it harder to pull the information, then skip it.  It's the rating and rank that are most important to me.

How...how in the world would I do this?

---

### Post by ~LoKe on 2007-12-29
Anyone?

---

### Post by dlegend on 2007-12-29
The language would have to have support for string parsing / manipulation as well as support to request data from the site. It'd be too much work for me to actually write the code (I'm a programmer but have mostly dealt with languages in Windows, with the exception of PHP), but basically it would be all string manipulation.

Find common attributes and use those to loop through entries. EG:

> 
	<tr>
		<td class='cell-first'>&nbsp;</td>
		<td class='cell'>1</td>
		<td class='cell' style="text-align:left"><table class="table" cellspacing=0 cellpadding=0><tr><td style="width:18px;padding-right:5px;padding-top:2px"></td><td style="f_ont-variant:small-caps"><a title="/ss/z|708090" href='?mod=playerinfo&idx=28492737'><FONT STYLE="color:#FFFFFF"><FONT STYLE="color:#585858">/<FONT STYLE="color:#00FF00">SS<FONT STYLE="color:#585858">/<FONT STYLE="color:#FF0000">Z<FONT STYLE="color:#FFFFFF">|<FONT STYLE="color:#FF7F00">708090</FONT></FONT></FONT></FONT></FONT></FONT></FONT></a></td></tr></table></td>

		<td class='cell'><span class="rating_equal">20.41</span></td>
		<td class='cell'>53.3 hrs</td>
		<td class='cell'>29 ms</td>
		<td class='cell'>44h</td>
	</tr>


That is one entity. If you want the person's rank info based on what their name is it wouldn't be too hard. Their name is seen in the "title" attribute - eg:

> 
<a title="/ss/z|708090" href='?mod=playerinfo&idx=28492737'>


So say you searched their name. It would find/save the location of /ss/z|708090 using a variable. It'd then find the last occurrence of "<tr>" by searching backwards from that location. By doing so you can locate the start of the entity. You'd then look for the next occurrence of "</tr>" going forward to locate the end of the entity.

From then on it's all about parsing the data by using string functions to locate certain parts of the data within the entity. Basically you just need all the right numbers and things to look for to parse the data how you want.

I think perl would do the trick but I haven't done any perl. Good luck =)

---

### Post by ~LoKe on 2007-12-29
Hm...some good information there.  Now I have somewhere to start!

Which parameters do I have to pass through wget in order to process the document in the first place?

---

### Post by dlegend on 2007-12-30
> **~LoKe said:**
> Hm...some good information there.  Now I have somewhere to start!

Which parameters do I have to pass through wget in order to process the document in the first place?

Type in "man wget" in the console for documentation. A basic example is simply:

> 
wget [http://www.google.com](http://www.google.com)


The above example would save index.html into your home directory. 

I found -O or --output-document= will let you choose where to save the output of the HTML. Here's an example that would work:

> 
wget [http://www.google.com](http://www.google.com) --output-document=process.html

or

wget [http://www.google.com](http://www.google.com) -O process.html


The above would save the data to process.html in your home user directory. From there you would parse the data from the saved file as I explained earlier.

---

### Post by ~LoKe on 2007-12-30
I gave those a shot, but when I wget [this](http://et.splatterladder.com/?mod=serverinfo&idx=311229&section=ranking) page, it just downloads a small portion of the document.  The rankings are missing, probably because it's a php page which would use include's and require's.

Maybe it's not possible.  But thanks for all the help!

---

### Post by dlegend on 2007-12-30
> **~LoKe said:**
> I gave those a shot, but when I wget [this](http://et.splatterladder.com/?mod=serverinfo&idx=311229&section=ranking) page, it just downloads a small portion of the document.  The rankings are missing, probably because it's a php page which would use include's and require's.

Maybe it's not possible.  But thanks for all the help!

The includes / requires have nothing to do with it. Those are dealt with on the server and will be included in wget. I think I found your problem:

In the URL there are "&" symbols. Try the following command:

```

wget http://et.splatterladder.com/?mod=serverinfo\&idx=311229\&section=ranking -O rankdata.html

```

Using a backslash "\" allows the ampersand symbol "&" to be used in the URL. Otherwise the URL will be cutoff preventing you from requesting the proper URL. Let me know if it works.

---

### Post by ~LoKe on 2007-12-30
*smacks self*

That did it.  Now I shouldn't have a problem pulling the info from it.

Thanks so much!

---

