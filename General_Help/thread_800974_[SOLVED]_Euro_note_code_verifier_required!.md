---
title: "[SOLVED] Euro note code verifier required!"
date: 2008-05-20
forum: General Help
---

### Post by Rytron on 2008-05-20
Hi 
I use Euro as currency. I recently covered checksums in college. The various checksums covered Euro Note and Credit Card number verification methods. There are many sites to help someone verify that a credit card is authentic, however there seems to be no on line verification tool for Euro notes. It would be even better to have a JavaScript program that could do this, then you could check off line.

This is how to verify a Euro note:
Convert the first letter to a number.
Then add up all the numbers and the letter which is now converted to a number.
What ever the total is, the numbers must result in 8 in order for that Euro note to be authentic. (For example this [note]("http://www.vision.net.au/~pwood/Volume167.jpg") has a total of 71, then 7 + 1 = 8 therefore this is authentic.)

Such a verification tool would be very useful for shop owners.

If anyone is smart enough to make a JavaScript program to verify the validity of a Euro bank note, please post a link here.
Or please post the code.

I'd greatly appreciate it.

Also one last thing, if someone could come up with JavaScript code to calculate this: [http://en.wikipedia.org/wiki/PPS_number]("http://en.wikipedia.org/wiki/PPS_number") it would be wonderful.

Cheers.

---

### Post by Rytron on 2008-05-20
Here is a convenient lookup table I made.

---

### Post by jespdj on 2008-05-20
Is this a covered up request to let someone else do your homework?

---

### Post by Rytron on 2008-05-20
> **jespdj said:**
> Is this a covered up request to let someone else do your homework?

No, my exams are over.

---

### Post by Rytron on 2008-06-18
I got help on another forum.
The user who helped me was PC-XT.

Here it is:

[B]<html>
<head>
</head>
<body>

<script>
function euroIsValid(num){var t,n,i,c;
 if(num.length<12)return false;//added min length
 t=num.substring(0,1).toUpperCase().charCodeAt(0)-64;//charCodeAt() requires 4.0 browsers
 if(t<1||t>26)return false;//doesn't begin w/ letter
 n=num.substring(1);
 while(n.length>1){
  for(i=0;i<n.length;i++)if(isNaN(c=parseInt(n.charAt(i))))return false; else t+=c;
  n=t.toString();t=0;
 }
 return(parseInt(n)==8);
}

//simple validation:
t=prompt("Please enter the Euro note's code number:\n(no spaces, please)","");
if(t!==null){
 if(euroIsValid(t))document.write("The Euro note code number, "+t+", checks out ok.");
 else{
  document.write(t+" is a <font color=red size=5>Counterfeit Euro!</font>");
  if(t.length<12)document.write("<br>The code should be longer.");
  else document.write("<br>The checksum doesn't check out.");
}}else document.write("User cancelled verification.");
</script>
<p>Refresh this page to try another code.
</body>
</html>[/B]

---

