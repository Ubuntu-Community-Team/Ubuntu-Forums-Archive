---
title: "[SOLVED] PHP Server Images"
date: 2008-06-24
forum: General Help
---

### Post by CrusaderAD on 2008-06-24
I'm using the following script but it isn't displaying the images, just the names, something is wrong with the syntax on the img src line:


<b><center>Our Best Selling Health Products:</center></b><P>

<?
include("config.php");
$result = mysql_query("select * from bestsellers ORDER by rank ASC") or die (mysql_error()); 
while ($row = mysql_fetch_array($result))
{

$sql = "SELECT name,description,image,brand,our_price,package_type
	    FROM evitamins_products
	    WHERE skew = '$row[skew]'
	";
$query = mysql_query($sql);
$fetch = mysql_fetch_array($query);

// Strip out all html in description for short descriptions
$description = strip_tags($fetch[1], '');

// Now limit the processed description tag to only 200 characters
$description2=substr($description, 0, 200);

echo "
<table border=0 cellpadding=2 bgcolor=#ffffff align=center cellspacing=0 width=100%>
<TR>
<TD align=right width=12% bgcolor=#ffffff valign=top>
<a href=\"product.php?skew=$row[skew]\">
<img src=\"=$fetch[2]&sharpenvalue=&Rotate=0\" border=\"0\" alt=\"$fetch[0]\" align=\"left\"></A>
</TD>
<TD align=left width=88% bgcolor=#ffffff valign=top>
<a href=\"product.php?skew=$row[skew]\">$fetch[0]</A><br>
Made By: <a href=\"brand.php?brandname=$fetch[3]\">$fetch[3]</A><br>
$$fetch[4] For $fetch[5]<br>
$description2... <a href=\"product.php?skew=$row[skew]\">More Info >>></A>
</TR></TD></Table>
<HR width=98% color=#000000 align=center><br>
";
}
mysql_free_result($result);
?>


If I apply quotes, it gives me a syntax error. What is wrong?

---

### Post by Gunman1982 on 2008-06-24
Didn't you ask something similar about some hours ago? *puzzled*
I don't know why you would need additional post variables in an image tag
```
<img src=\"=$fetch[2]&sharpenvalue=&Rotate=0\" border=\"0\" alt=\"$fetch[0]\" align=\"left\"></A>
```
try this instead:
```
<img src=\"$fetch[2]\" border=\"0\" alt=\"$fetch[0]\" align=\"left\"></A>
```
Could be that you have to url_encode those values though.

---

### Post by CrusaderAD on 2008-06-24
Thank you sir. That solved it!

---

