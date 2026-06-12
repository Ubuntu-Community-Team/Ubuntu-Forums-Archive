---
title: "Firefox input types messed up"
date: 2007-05-12
forum: General Help
---

### Post by rydar on 2007-05-12
Hi,

I installed ubuntu fiesty fawn and just recently I had this issue where all the form input types in firefox showed up like the screenshot. Was wondering if anyone might be able to help. Not sure what I did to do it but it got messed up some how. I've tried reinstalling it from synaptic but it always has the same result.

here is what the html code i used to get the screenshot.

> 

<html>
<head>
<title>Firefox input type bug??</title>
</head>
<body>
	<table width="500" align="center">
		<tr>
			<td>
				<table width="100%">
					<tr>
						<td>Buttons:</td>
						<td><input type="button" value="Button 1"> <input type="submit" value="Submit Button"></td>	
					</tr>
					<tr>
						<td>Input Text Box:</td>
						<td><input type="text" value="This is some text" size="30"></td>
					</tr>
					<tr>
						<td>Select List:</td>
						<td>
							<select>
								<option value="1">Value 1</option>
								<option value="2">Value 2</option>
								<option value="3">Value 3</option>
							</select>
						</td>
					</tr>
			</td>
		</tr>
	</table> 
</body>



---

### Post by rydar on 2007-05-12
Ok got it fixed. Must have been a bad extension I installed.

ran this in the console, then deleted the current profile and deleted all the files and created a new default profile.
firefox -ProfileManager

now everything is working :)

---

