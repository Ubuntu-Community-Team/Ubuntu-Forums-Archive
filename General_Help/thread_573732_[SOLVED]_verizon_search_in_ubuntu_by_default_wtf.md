---
title: "[SOLVED] verizon search in ubuntu? by default? wtf?"
date: 2007-10-11
forum: General Help
---

### Post by peppy on 2007-10-11
I am using Gutsy beta with Firefox and today after an upgrade to 2.0.0.6 I noticed when typing a word into the address bar instead of taking us to google search it takes us to a verizon.net websearch.

example a search for dogs in the address bar:
[http://wwwwz.websearch.verizon.net/search?qo=dogs&rn=ByLV-OazrDJ5fzO](http://wwwwz.websearch.verizon.net/search?qo=dogs&rn=ByLV-OazrDJ5fzO)

I also just did a fresh install on my partners computer, macbook, many improvements btw: and there is the same verizon.net search.

now when i use firefox 2.0.0.3 in windows (in vmware on the same machine) it uses the regular google search.

I am going to try using firefox 2.0.0.7 (windows-vmware) in a few moments  to see what the results are.

I have also cleared my cache, removed cookies and whatnot.

my question is --- whats the deal? it doesn't seem to be the network, it seems to be a configuration that is specific to ubuntu.



I was wrong... it was the network I found "about this page" in the search
> 
About the Search Results Page

You reached the preceding search results page because Verizon is using specific Domain Name Service (DNS) Servers to look up domain names. These DNS Servers eliminate dead-end "no such name" error pages you can encounter as you surf the web. This search service is designed to make your web surfing experience more productive. No software was installed on your computer for this service to work.

&#8226;  What is DNS
All Web sites have an address that consists of a series of numbers separated by periods, such as 153.39.1.1. This is known as an IP address. Most Web sites also have a domain name (such as [www.verizon.net](www.verizon.net)) associated with their IP address. With DNS, users don't have to type the complicated IP address into their browser's address bar; instead, they can type the domain name. DNS then acts like a real-time phonebook, looking up the name entered and translating it into the numbers that the computer recognizes so that the desired Web site can be displayed.

---

