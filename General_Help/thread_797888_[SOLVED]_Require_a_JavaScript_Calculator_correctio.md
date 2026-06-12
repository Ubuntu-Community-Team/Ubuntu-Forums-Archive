---
title: "[SOLVED] Require a JavaScript Calculator correction!"
date: 2008-05-17
forum: General Help
---

### Post by Rytron on 2008-05-17
Hi,
I need this calculator to add two numbers. They don't add them, but instead concatenate them.
What should I do? Thanks.

[B]```
<html>

<head><title>JS</title>
</head>

<body>

<script type="text/javascript">

var numb1=prompt("number 1: ");
var numb2=prompt("number 2: ");
document.write(numb1 + numb2);

</script>

</body>

</html>
```[/B]

---

### Post by drskol on 2008-05-17
You need to convert the information you gathered from the prompts to integers; then the '+' operator will do an addition. In the following snippet the parseInt() function acts on the input from the prompt() and your variables are treated as numbers then:

```

var numb1=parseInt(prompt("number 1: "));
var numb2=parseInt(prompt("number 2: "));

```

---

