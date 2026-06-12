---
title: "HOW-TO: Search Ubuntu Forums quickly in Firefox Search Bar"
date: 2007-10-24
forum: General Help
---

### Post by superyounan1 on 2007-10-24
You can use [http://mycroft.mozdev.org/]("http://mycroft.mozdev.org/") to add a search link to the forum.

But I prefer using google to search ubuntuforums, tends to give better results and avoids that annoying 15 second wait in between searches, heres how i did it

create a new text file "ubuntuforums.xml" on your Desktop, for example, and paste the contents:

```

<?xml version="1.0" encoding="UTF-8"?>
<OpenSearchDescription xmlns="http://a9.com/-/spec/opensearch/1.1/">
  <ShortName>Ubuntu Forums</ShortName>
  <Description>Use Google to Search Ubuntu Forums</Description>
  <Url type="text/html" 
       method="get"
       template="http://www.google.com/search?q=site%3Aubuntuforums.org+{searchTerms}">
  </Url>
  <LongName>Ubuntu Forums Search with Google</LongName>
  <Image height="16" width="16" type="image/vnd.microsoft.icon">http://www.ubuntu.com//themes/ubuntu07/favicon.ico</Image>
  <Query role="example" searchTerms="Technorati" />
  <Developer>Younan</Developer>
  <SyndicationRight>open</SyndicationRight>
  <AdultContent>false</AdultContent>
  <Language>en-us</Language>
  <OutputEncoding>UTF-8</OutputEncoding>
  <InputEncoding>UTF-8</InputEncoding>
</OpenSearchDescription>

```

upload the file to a server, if you have apache installed this should be trivial, and paste the javascript snippet bellow into firefox's address bar:
```

javascript:window.external.AddSearchProvider('http://URL_TO_FILE/ubuntuforums.xml');

```

[COLOR="Red"]EDIT[/COLOR]: I originally suggested saving the file locally somewhere and had the URL set to "file:///path_to_file..." etc., but It seems that this method doesn't work with firefox, so it will need to be passed through http. If you have a web server, such as apache installed, then just put the file in one of the aliased directories and link to it. I might post it on my server for ease soon.

It should work in IE7 if by any chance you were wondering

---

