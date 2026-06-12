---
title: "How to store &lt;li&gt; form a HTML in a variable with curl."
date: 2014-01-20
forum: General Help
---

### Post by Raymundo_Gabriel on 2014-01-20
Hi, I am new to this bash stuff and I really need to find out how to make a bash program to do the following tasks.

i have an HTML page which I have to gather some information from it, but it's very boring to copy and paste all the information, I started to look at the basic HTML file from that web page and realized that they have all those information order by class and ids.

What I have till now is : 

curl the_web_page_link | grep "class=\"adress-id\""    

this shows me the Information than i want, but I need to store this  information to a file, and also it's not all the information I need, I need to make like a database with the first class of the webpage witch is name, then the adress, and then the phone. Seems like curl help me but grep don't.

the webpage order is this one :

<li>
<span class = "name-id"> here is a  blank line and then in the other line is the information about the name</span>
<span class = "adress-id"> adress information   </span>
<span class = "phone-id"> phone information   </span>



</li>


im new to this forum and also from Mexico, I hope you had understood me and thanks for help

---

