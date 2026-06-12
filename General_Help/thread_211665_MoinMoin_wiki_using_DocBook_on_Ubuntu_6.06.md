---
title: "MoinMoin wiki using DocBook on Ubuntu 6.06"
date: 2006-07-08
forum: General Help
---

### Post by AllBuntu on 2006-07-08
1. Under Ubuntu 6.06 I did the following: 
```
sudo apt-get install python-4suite ### get the xslt parser
sudo nano /etc/moin/mywiki.py ### the configuration file for the wiki in question
### insert a line " allow_xslt = 1" just above the "data_dir" statement
### at the same place, insert a line " docbook_html_dir = '/usr/share/moin/mywiki/data/html'"
### a) browse to [http://sourceforge.net/projects/docbook/](http://sourceforge.net/projects/docbook/)
### b) download the latest 'dockbook-xsl' zip and unpack it to your desktop
### now install into a writable wiki directory
sudo cp -R ~/Desktop/docbook-xsl-1.70.1/html /usr/share/moin/mywiki/data ### assuming this is where your wiki is at
sudo chown -R www-data.www-data /usr/share/moin/mywiki/data/html ### make writable to moin/apache2
```
2. Text docbook source format: create wiki page with the below exact text (ref. moinmoijn site [http://moinmoin.wikiwikiweb.de/HelpOnXmlPages](http://moinmoin.wikiwikiweb.de/HelpOnXmlPages)) 
```
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE book PUBLIC "-//OASIS//DTD DocBook XML V4.4//EN"
"http://www.oasis-open.org/docbook/xml/4.4/docbookx.dtd">
<book>
  <title>Title of my next book</title>
  <chapter>
    <title>Chapter Title</title>
    <section>
      <title>First Heading</title>
      <para>Some Text</para>
    </section>
  </chapter>
</book>
```
3. Issue 1 with the above example that has no stylesheet reference I get an error message: 
```
XSLT processing error: No stylesheets to process.
```
4. Issue 2 with the below stylesheet reference, I get 
```

<?xml-stylesheet href="docbook.xsl" type="text/xml"?>

XSLT processing error: Error retrieving resource u'wiki://Self/docbook.xsl': Page does not exist
```
Please, how can I fix this, if you could provide very detailed instructions? I think a key might be the cryptic statement HelpOnXmlPages "After you have upgraded 4suite, you have to delete the file db_compiled.dat in this directory." that I don't understand. You may refer to a required update to the 4ss repository or something?

5. For something that does work, I also tried to download the XMLMind XML editor, went for the file C:\docbook\xsl\html\docbook.xsl with everything it includes and published that on the Internet. I then created the following wiki page: 
```
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE book PUBLIC "-//OASIS//DTD DocBook XML V4.4//EN"
"http://www.oasis-open.org/docbook/xml/4.4/docbookx.dtd">
<?xml-stylesheet href="http://somewebsite.com/html/docbook.xsl" type="text/xml"?>
<book>
  <title>Title of my next book</title>
  <chapter>
    <title>Chapter Title</title>
    <section>
      <title>First Heading</title>
      <para>Some Text</para>
    </section>
  </chapter>
</book>
```
...and it comes out great!
However, that save takes 55 seconds.
I also tried copying this second style sheet onto the file system, but it does not work.

keywords: moin moinmoin wiki docbook xslt 4ss 4suite python

---

