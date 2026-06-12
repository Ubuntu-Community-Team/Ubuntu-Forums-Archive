---
title: "unable to view website"
date: 2006-09-12
forum: General Help
---

### Post by dasuberdog on 2006-09-12
So far I have never had a problem viewing a website.  [http://www.pfglaw.com/](http://www.pfglaw.com/)

This website I can see the entry page but once you "click to enter"  all I get is html code.  The website works fine on windows computers.  Is there some firefox plugin I am missing?

Thanks

---

### Post by Lord Illidan on 2006-09-12
I too am unable to see the site with Konqueror or Firefox.

I think it is a problem on their end.

look at the source:

[I]body {
	font-family: Verdana, Geneva, Helvetica, Arial, sans-serif;
	font-size: 8.5pt;
	margin:0px 0px; padding:0px; /* Need to set body margin and padding to get consistency between browsers. */
	text-align:center; [COLOR=Red]/* Hack for IE5/Win */[/COLOR]
	}
	
#Content {
	width: 768px;
	margin:0px auto; /* Right and left margin widths set to "auto" */
	text-align:left; [COLOR=Red]/* Counteract to IE5/Win Hack */[/COLOR]
	padding:0px;
	border:0px;
	}[/I]

---

### Post by nrwilk on 2006-09-12
> **Lord Illidan said:**
> I think it is a problem on their end.

You're correct.  It has nothing to do with ubuntu or firefox.  It's a mess-up on the site's side.

They'll catch it soon enough and fix it.  Or, if you can find an email address for the site's webmaster, you could send a letter there to alert them to the problem.

---

