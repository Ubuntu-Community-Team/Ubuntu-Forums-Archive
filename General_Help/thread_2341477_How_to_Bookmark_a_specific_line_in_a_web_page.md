---
title: "How to Bookmark a specific line in a web page ?"
date: 2016-10-28
forum: General Help
---

### Post by shantiq on 2016-10-28
...say you read a very long article/webpage over a period of days ...   and you want to bookmark the line in the text you need to pick up in your reading


is there a tool or an easy way to do this?   googling yields nothing that i can see
it seems such a basic need of any reader/student/web user/etc


how do you deal with this?


======

only trick i can think of which is not really a tool is to copy and save the line in question in a text editor and then to open your webpage and do CTRL+F   and enter the line and do this  each session
This works perfect but is hardly hitech

======


Suggestions?

---

### Post by TheFu on 2016-10-28
If there is a "name" tag inside the HTML, you can set a bookmark on that.  Sometimes they are at every header, but it just depends on what the page developer did. You and I don't really have any control over that - at least not while the web page is on their server.

Probably more effort than you'd like, but ... I've been using something called wallabag to store webpages for reading later. It has a way to highlight stuff, which might be sufficient for your needs. It is a php server, so you'd need to run a LAMP stack.  Basically, it is read-it-later without all the tracking and available on my local network. There are android apps which replicate the data for off-line reading too.  Plus it estimates how long every article is to read, so I can select which articles to read based on the time available.

You can also move the page into a local copy for note taking - Lots of programs for that.  Look for something like evernote and BasketNotes.  Might find something useful there. 

For very long text files that I can edit, I add **:TODO:** markers where I leave off or where something needs modifying. It is an old trick that software developers use ... other tags are used too  :BUG: , :TRICKY:, :FIX: ... you get the idea.

These certainly aren't all the possible ways and I bet other people deal with it in smart ways too.

---

### Post by CantankRus on 2016-10-28
I use  a chrome extension called [**_[COLOR="#B22222"]webtags[/COLOR]_**]("https://chrome.google.com/webstore/detail/webtags/afbnmadfcpjkmhflfehokhohdgnbladp").
Highlight a phrase and by right click you can save that phrase to webtags.
[ATTACH=CONFIG]271824[/ATTACH]

Then when you open the same page again, hit the icon in the address bar to take you to the highlight.
[ATTACH=CONFIG]271825[/ATTACH]

---

### Post by shantiq on 2016-10-28
hmmm   Thanx Fu    some interesting ideas    ....    amazing how ths has never really been addressed as a priority when surely we all need this  ...   there are still huge omissions in our new cyber-reality  ....    come to think of it  paper bookmarks do not either keep the line :]   in a paper book

---

### Post by shantiq on 2016-10-28
> **CantankRus said:**
> I use  a chrome extension called [**_[COLOR=#B22222]webtags[/COLOR]_**]("https://chrome.google.com/webstore/detail/webtags/afbnmadfcpjkmhflfehokhohdgnbladp").
Highlight a phrase and by right click you can save that phrase to webtags.


Thanx C This is exactly what i need and i had found it but only works with Chrome[ium]  and I use Palemoon  but good for Chrome[ium]  altho i cannot get it to work on this page in Chromium
[http://www.h-net.org/~hst306/documents/huron.html](http://www.h-net.org/~hst306/documents/huron.html)

---

### Post by TheFu on 2016-10-28
> **shantiq said:**
> hmmm   Thanx Fu    some interesting ideas    ....    amazing how ths has never really been addressed as a priority when surely we all need this  ...   there are still huge omissions in our new cyber-reality  ....    come to think of it  paper bookmarks do not either keep the line :]   in a paper book

In a paper book, I use those "sign here" tabs to point to the line. The little flaps work nicely.

I worked in electronic documentation for a few years, but we concentrated on PDF files and making those work as close to paper as possible with all the added things electronic versions allow. 

Like that addon from CantankRus too!  Wasn't able to find a version for firefox in a quick search.  Guess I'm stuck with wallabag annotations - which work nicely.

---

### Post by vasa1 on 2016-10-28
How close does [https://addons.mozilla.org/en-US/firefox/addon/advanced-bookmaks-add-on/](https://addons.mozilla.org/en-US/firefox/addon/advanced-bookmaks-add-on/) come? I don't use it and given how fast things break, I'm not sure it even works with the latest Firefox.
> This addon will let you to save bookmark with position in web page, or with select text that allow you to open the page and automatically scroll to position, or select text.

---

### Post by shantiq on 2016-10-29
Hi Vasa and thanx for link but does nothing on Palemoon and although it appears on FF   does not seem to work  ...   maybe as i use LXDE  ...   I don't know :]

---

### Post by CantankRus on 2016-10-30
Does greasemonkey  work with Palemoon?
This [userscript]("https://greasyfork.org/en/scripts/3199-in-page-bookmark/code") works here in firefox.
It's in Chinese but with a little help from google-translate I altered the buttons to English.
Puts an expandable tab to the right of webpage where you can store page position.

---

### Post by shantiq on 2016-10-30
Cool CantankRus.   Palemoon does not accept Greasemonkey as it says wrong version of FF
But I am testing it on FF anyhow to see how it performs

and yes   nice one

I think it is permissible to translate and add to the store of scripts is it not [or are they not open source]?   maybe you could add it if you wish to would be good for all English users

I do not see how you managed to change the 2 Chinese words; it does not let me edit here [maybe I need to add Chinese to my languages on computer];   but no biggie  ...   other slight irk is that it returns it to the exact position on the page  you left it last so you have to remember that or you have to scan the screen page to find it again;   but certainly the best so far;  if it always brought the saved line on resumption to the top of the screen that would be much better would it not? :]

HA   the penny drops :  obviously position the line at top of screen before saving THEN   it will appear at top again on resumption

So thank you for that C

&#10112;  install [greasemonkey]("https://addons.mozilla.org/en-gb/firefox/addon/greasemonkey/") and load [script]("https://greasyfork.org/en/scripts/3199-in-page-bookmark/code")
&#10113; see images below to help understand and also previous ones posted by CantankRus
&#10114; then finally click your saved line in pop-out box on the right and it will bring the line to where you had left it last [obviously position the line at top of screen before savin THEN   it will appear at top again on resumption]


[ATTACH=CONFIG]271865[/ATTACH][ATTACH=CONFIG]271866[/ATTACH][ATTACH=CONFIG]271867[/ATTACH][ATTACH=CONFIG]271868[/ATTACH]




PS    as regards Palemoon still using CTRL+F plus text editor   but hey  we are getting there :]

---

### Post by CantankRus on 2016-10-30
Here is my translated script.
Save as **Pager.user.js** and drag and drop into firefox where greasemonkey should intercept.
It won't override the original so you will need to disable the In-Page script.
```
&#65279;// ==UserScript==
// @name        Pager
// @namespace   org.jixun.bookmark
// @description Pager, translated from: Tieba#3114763315 & GreasyFork#2676
// @include     *
// @version     1.0.2
// @grant       unsafeWindow
// @run-at      document-start
// ==/UserScript==


var moduleBookmark = function () {
	try {
		this.init();
	} catch (e) {
		console.error ('org.jixun.bookmark: init failed :<', e);
	}
};
moduleBookmark.prototype = {
	extract: function (foo) {
		return foo.toString().replace(/--.+/g, '').match(/\/\*([\s\S]+)\*\//)[1];
	},

	attr: function (node, name, val) {
		if (arguments.length === 2) {
			if (name instanceof Object) {
				for (var x in name)
					if (name.hasOwnProperty (x))
						node.setAttribute (x, name[x]);
				
				return ;
			}
		
			var ret = node.getAttribute (name);
			try {
				return JSON.parse (ret);
			} catch (e) {
				return ret;
			}
		}
		
		if (val instanceof Object)
			val = JSON.stringify (val);

		node.setAttribute (name, val);
	},

	create: function (el, text, attr) {
		var r = document.createElement (el || 'div');
		if (text) r.textContent = text;
		
		// quick config
		if (attr instanceof Object)
			this.attr (r, attr);
		
		return r;
	},

	setBookmarks: function (o) {
		localStorage['jjwt_' + location.pathname] = JSON.stringify (o);
	},

	getBookmarks: function () {
		try {
			return JSON.parse(localStorage['jjwt_' + location.pathname]);
		} catch (e) {
			return [];
		}
	},
	
	// add and save bookmarks
	addMark: function (yPos, name) {
		var bm = this.getBookmarks(),
			defName = 'unnamed #' + bm.length;
		
		if (!name) {
			name = prompt ('Please enter bookmark name, Leave blank to use default:', defName);

			// user clicks cancel
			if (null === name)
				return ;

			// bookmarks are empty
			if (!name)
				name = defName;
		}
		
		bm.push ([
			typeof yPos == 'number' ?
				yPos : unsafeWindow.pageYOffset,
			
			name
		]);
		this.setBookmarks (bm);
		this.updMark ();
	},
	
	updMark: function () {
		// rebuild bookmarks
		this.lstBookmark.innerHTML = '';
		
		var that = this;
		this.getBookmarks ().forEach (function (mark, i) {
			// [location, name]
			var li = that.create ('li');
			var linkGo  = that.create ('a', mark[1], {
				type: 'go',
				ypos: mark[0]
			});
			var linkDel = that.create ('a', 'delete',  {
				type: 'rm',
				line: i
			});
			
			[	linkGo,
				document.createTextNode (' [ '),
				linkDel,
				document.createTextNode (' ]')
			].forEach (li.appendChild.bind (li));
			that.lstBookmark.appendChild (li);
		});
	},

	init: function () {
		// create div
		this.bm  = this.create ();
		this.nav = this.create ();
		this.main= this.create ();
		
		this.bm.id = 'jjwtBookMark';
		this.nav .className = 'bmNav';
		this.main.className = 'bmMain';
		
		//Add [Pager]
		this.h3  = this.create ('h3', 'Pager');
		this.main.appendChild (this.h3 );
		this.h3a = this.create ('span', '');
		this.nav .appendChild (this.h3a);
		
		// Add [Bookmark] button
		this.btnAddBookmark = this.create ('button', 'Add');
		this.btnAddBookmark.onclick = this.addMark.bind (this, null, null);
		this.main.appendChild(this.btnAddBookmark);
		
		// create [bookmark list]
		this.lstBookmark = this.create ('ul');
		this.main.appendChild(this.lstBookmark);
		
		this.bm.appendChild (this.nav );
		this.bm.appendChild (this.main);
		document.body.appendChild (this.bm);
		
		// create defaault label
		if (this.getBookmarks().length === 0)
			this.addMark (0, 'Top of Page');
		
		// refresh tab bar
		this.updMark ();
		
		this.lstBookmark
			.addEventListener ('click', this.markClick.bind (this), false);

		this.addStyle ();
	},
	
	markClick: function (eve) {
		var el = eve.target;
		if (el.tagName !== 'A' || !el.hasAttribute ('type'))
			return ;
		
		switch (this.attr (el, 'type')) {
			case 'go':
				unsafeWindow.scrollTo (0, parseInt(this.attr (el, 'ypos')));
				break;
			case 'rm':
				var m = this.getBookmarks ();
				m.splice (parseInt(this.attr (el, 'line')), 1);
				this.setBookmarks (m);
				this.updMark ();
				break;
		}
	},
	
	addStyle: function () {
		if (this.css) return ;
		
		this.css = document.createElement ('style');
		this.css.textContent = this.extract (function () {/*
#jjwtBookMark {
	font-family: Ubuntu, 'Microsoft JHengHei UI', 'Microsoft YaHei UI', sans-serif;

	font-size: 12px;
	border: 1px solid #aaa;
	border-right: 0;

	z-index: 9999999999;
	background: #FFD;
	text-align:left !important;
	word-break: break-all;
	overflow: hidden;


	-- hover state
	width:  20px;

	-- &#40736;&#26631;&#31227;&#24320;, &#22238;&#25910;&#21015;&#34920;&#30340;&#26102;&#38271;&#20026; 0.3s
	transition: width .3s ease;
	
	-- &#23450;&#20301;, &#27704;&#36828;&#23621;&#20013;&#20110;&#39029;&#38754;
	top: 50%;
	height: 80px;
	margin-top: -40px;
	-- &#23450;&#20301;, &#22266;&#23450;&#21040;&#21491;&#36793;
	right: 0;
	position: fixed;
}
#jjwtBookMark:hover {
	-- &#37325;&#32622;&#23450;&#20301;&#33267;&#21491;&#36793;, &#22635;&#28385;&#25972;&#20010;&#39640;&#24230;
	margin-top: 0;
	top: 0;
	width: 20em;
	height: 100%;

	-- &#24748;&#28014;, &#19978;&#19979;&#20004;&#26465;&#36793;&#19981;&#38656;&#35201;
	border-top: 0;
	border-bottom: 0;

	-- &#24748;&#28014;, &#23637;&#24320;&#21015;&#34920;&#30340;&#26102;&#38271;&#20026; 0.3s
	transition-duration: .7s;
}

-- &#32553;&#23567;&#26102;&#26174;&#31034;&#30340;&#26631;&#39064;
#jjwtBookMark > .bmNav {
	width: 20px;
	word-break:break-all;
	text-align: center;

	line-height: 1.3;
	padding: 7px 0;
}
#jjwtBookMark:hover > .bmNav {
	display: none;
}

-- &#20070;&#31614;&#26412;&#20307;
#jjwtBookMark > .bmMain {
	display: none;
	position: absolute;
	word-break:break-all;
	width: 20em;
}
#jjwtBookMark:hover > .bmMain {
	display: block;
}

#jjwtBookMark h3 {
	padding: 0.5em;
	margin:  0;
	display: inline-block;
	font-size: large;
}

#jjwtBookMark ul {
	list-style: square inside none;
	padding: 0.5em 0;
	margin-left: 0.5em;
	padding-bottom: 0;

	-webkit-user-select: none;
	-moz-user-select: none;
	user-select: none;
} 
#jjwtBookMark li {
	list-style: inherit;
}
#jjwtBookMark li > a {
	cursor: pointer;
}
		*/});
		document.head.appendChild (this.css);
	},
	
};

addEventListener ('DOMContentLoaded', function () {
	console.info ('org.jixun.bookmark: Ready to go.');
	new moduleBookmark ();
}, false);
```

---

### Post by shantiq on 2016-10-30
ACE!

yes save as a new script on your computer


*** and yes to save line of text when positioned at top of screen then it is a perfect tool***


thanx C


PS   i am sure you can upload it with all credits given; it will help many



[ATTACH=CONFIG]271871[/ATTACH]

---

### Post by CantankRus on 2016-10-30
> **shantiq said:**
> ACE!

even easier to save as a new script on your computer


and yes to save line of text when positioned at top of screen then it is a perfect tool


thanx C


PS   i am sure you can upload it with all credits given; it will help many



[ATTACH=CONFIG]271871[/ATTACH]
Yes, I should do.
If you're just using as a place holder, you don't even have to highlight text.
Just hit the Add button and then "OK" and it will save the current position as "unnamed #1".
It will auto number as added.

If you want you can change "unnamed" in the script to "Bookmark" to look better.

---

### Post by shantiq on 2016-10-30
really good :]

---

