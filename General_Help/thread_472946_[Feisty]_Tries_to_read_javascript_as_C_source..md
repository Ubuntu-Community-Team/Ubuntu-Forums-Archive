---
title: "[Feisty] Tries to read javascript as C source."
date: 2007-06-13
forum: General Help
---

### Post by Snakiej on 2007-06-13
Hiya, 

I've got a javascript file in /var/www, but whenever I try to open it via Nautilus, it says it is actually a C Source file, and I should change the extension to the correct extension for that file type.

But it is actually a javascript, with just this code inside:
```
/*
 * Functie om door alle href's te loopen, en bij diegene met http ervoor een onclick toe te voegen, zodat ze openen in een nieuw venster
 * Dit mag niet van XHTML, maar hier valt hij niet over, + het is proper.
 */
	
function parse_urls()
{
	doc = document.getElementsByTagName("a");
	//alert(doc.length);
	for (x = 0; x < doc.length; x++)
	{
		if(doc[x].getAttribute("href").indexOf("http") != -1)
		{
			//alert(doc[x].getAttribute('href'));
			doc[x].setAttribute("onclick","window.open(this.href); return false;");
		}
		//alert(doc[x]);
	}
}
```
Anyway to force it to remember that it is a .js file?

---

### Post by haricharan on 2007-06-13
what is the original extension of the file if not .js ?

---

### Post by Snakiej on 2007-06-13
> **haricharan said:**
> what is the original extension of the file if not .js ?

it is .js

I even created a new file, ahref.js , but still the same problem.

---

