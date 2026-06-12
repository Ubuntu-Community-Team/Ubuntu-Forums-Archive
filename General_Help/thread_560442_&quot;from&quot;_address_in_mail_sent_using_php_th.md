---
title: "&quot;from:&quot; address in mail sent using php through apache always shows as &quot;www-data@....&quot;"
date: 2007-09-26
forum: General Help
---

### Post by h3mp on 2007-09-26
I've been battling with this for 2 days and getting nowhere.... :(

I have a php script that sends mail using the mail() command - php.ini is configured for sendmail (using postfix)
I've set the "from" header correctly in my php script (works fine on a windows box) when trying under feisty server no matter what i do it sends from [email]www-admin@name-of-my.doma[/email]in.
I just need to change the www-admin bit - any ideas??

Thanks
Mark

---

### Post by Justin Trouble on 2008-02-13
Did you find a resolution?

I've just fixed my problem using Canonical Maps in Postfix

See [http://sysop.com.cn/document/Postfix.The.Definitive.Guide/0596002122_postfix-chp-4-sect-7.html](http://sysop.com.cn/document/Postfix.The.Definitive.Guide/0596002122_postfix-chp-4-sect-7.html)

4.7.1 Canonical Addresses

Postfix provides another type of address rewriting that lets you map disparate addresses into a standard format for your entire site. The canonical_maps parameter points to a lookup table of address mappings. (While the word canonical has many meanings, among computer professionals it means "the usual, standard, or normal.") If different mail systems on your network create addresses in different ways, you can relay them all through your Postfix gateway and have it fix up the addresses into your standard format. Canonical maps are often used to change addresses from an internal format to a public one. Include entries like the following in your canonical table:

#
# /etc/postfix/canonical
#
[email]pabelard@example.com[/email]   [email]peter.abelard@example.com[/email]
[email]hfulbert@example.com[/email]   [email]heloise.fulbert@example.com[/email]

They can also rewrite addresses completely.

#
# /etc/postfix/canonical
#
[email]pabelard@example.com[/email]   [email]abelard@oreilly.com[/email]
[email]hfulbert@example.com[/email]   [email]heloise@oreilly.com[/email]

In main.cf, point the canonical_maps parameter to the canonical file:

canonical_maps = hash:/etc/postfix/canonical

Be sure to execute postmap against your canonical file and reload Postfix so that it recognizes your changes to main.cf:

# postmap /etc/postfix/canonical
# postfix reload

The canonical_maps parameter affects all of the addresses, including envelope and message headers. If Postfix finds a match, it makes the change. If you want your changes to affect only sender or recipient addresses, Postfix provides the additional parameters sender_canonical_maps and recipient_canonical_maps. They both work the same as canonical_maps, but only on their respective classes of addresses. If you use either of these two parameters in addition to canonical_maps, Postfix first fixes the addresses according to sender_canonical_maps and recipient_canonical_maps, and then canonical_maps.

---

