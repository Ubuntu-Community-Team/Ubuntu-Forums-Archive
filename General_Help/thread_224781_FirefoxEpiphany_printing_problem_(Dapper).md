---
title: "Firefox/Epiphany printing problem (Dapper)"
date: 2006-07-28
forum: General Help
---

### Post by pitkali on 2006-07-28
Hi there,

I have problem with printing from Firefox and epiphany on Dapper (other applications have no problems at all - openoffice, acrobat reader, etc.) Forum and google search did not suggest any fixes.

Firefox: If I change paper size to a4size I get the message that this paper size is not supported by my printer. It is crap - I use only a4, always. And it did work under Breezy.

Epiphany: It doesn't say it is unsupported but it looks like it was using Letter size instead of A4. I set all print margins to 0 and it didn't help. Again - this used to workk under Breezy.

Perhaps I should note also that:
- the same version of firefox under windows has no problems,
- the printer is HP PSC 2355.

So - do you have any ideas what to do? Or should I just switch to Debian testing again... ? It would be such a pity..

Regards,
Piotr Kalinowski

---

### Post by gmatt on 2006-07-28
From what I understand and what my brother told me about the early phase of Dapper is that alot of things were broken that wren't previously so in Breezy because of newer security features among other things. My guess is that if you make enough noise about this issue then the devs will take a look. The squeaky wheel gets the grease. Try posting it in the Bugs section to bring it under the scrutiny of  the devs.

---

### Post by philippe_carlo on 2006-07-28
Is it a CUPS printer? Maybe look into cups configuration and check wether the paper size for the rinter is set correctly.

---

### Post by pitkali on 2006-07-28
> **philippe_carlo said:**
> Is it a CUPS printer? Maybe look into cups configuration and check wether the paper size for the rinter is set correctly.

Yes - it is the cups printer. The paper size is set correctly. Note that the problem arises only under the web browser.

---

### Post by pitkali on 2006-07-29
If anybody cares - here's how I overcame the problem under firefox (though I have no idea why it works):

- I printed a page to a file using Postscript/default as a driver.
- From now on it is possible to print and it works just fine. If you use CUPS printer the paper used will be the one configured as a  default - changing the paper size within firefox is not going to work, apparently.
You can also use Postscript/default 'printer' and enter custom print command -- this is how paper size change is still possible.

No success under epiphany though.

---

