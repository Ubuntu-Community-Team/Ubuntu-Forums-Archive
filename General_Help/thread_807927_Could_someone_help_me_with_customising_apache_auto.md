---
title: "Could someone help me with customising apache auto indexing?"
date: 2008-05-26
forum: General Help
---

### Post by marshall.robert on 2008-05-26
Hi, ive been trying to follow loads of different tutorials about customising the look of the indexing feature, so far all i can do is change the raw html used (where as i would like to use css), and the config stuff has been placed into httpd.conf as follows:

<Directory>
##RewriteEngine Off
IndexStyleSheet /style.css
AddType text/html .shtml
AddOutputFilter INCLUDES .shtml
Options Indexes Includes
IndexOptions FancyIndexing SuppressHTMLPreamble XHTML IconsAreLinks FoldersFirst SuppressDescription
HeaderName /header.shtml
ReadmeName /footer.shtml
</Directory>

the url of my server is [http://rob-server.co.uk]("http://rob-server.co.uk") and if you want to see the mighty specs go to [http://rob-server.co.uk/phpsysinfo]("http://rob-server.co.uk/phpsysinfo")

you may have guessed that im not completely competent with apache, but im getting there!

if anyone could help me achieve my goal then i would be very greatful!

Thanks in adavnce

-rob.


Edit: I commented out the RewriteEngine line since apache threw an error at me for it.

Edit 2: it appears that putting / infront of all my links, such as background images, and style sheets and so on seems to make it work....

---

