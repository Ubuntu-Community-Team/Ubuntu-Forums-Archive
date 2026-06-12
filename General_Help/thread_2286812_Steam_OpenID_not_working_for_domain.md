---
title: "Steam OpenID not working for domain"
date: 2015-07-14
forum: General Help
---

### Post by Randomguy55 on 2015-07-14
So I have some source files from a different site, when I try to sign in via steam on my site ([http://skinspinner.com/](http://skinspinner.com/)) it doesn't work and puts me on a white blank page with a massive url.
I have changed the url in UserController.php but it still doesn't work, however if I change it back to the website which the source files were being hosted in before, I can sign in to their site fine.

```
public function loginAction()	{
		if(isset($this->session->user->role)) {
			return $this->response->redirect();
		}
		// $site = 'localhost';
		$site = 'skinspinner.com';
		$OpenID = new LightOpenId($site);
		if(!$OpenID->mode) {
			$OpenID->identity = 'http://steamcommunity.com/openid';
			header('Location: ' . $OpenID->authUrl());
```

---

