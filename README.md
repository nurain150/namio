This is a solution to one of the Android CTF by hackerone.
The Oauth Bypass CTF.
Download the app From the CTF server ctf.hacker101.com.
Decompile the app with apktool,
Convert the sex file to jar classes with jadx or d2j or your suitable tool.
Open the source code.yayy it is set.
By installing and running the apk file.We discover that the app opens up a website in the browser with authenticat
By clicking it takes us back to the app with an authed message.(successful).
How about breaking the app logic.Since we know we need to capture the flag.
Running an inspect element on the redirect website.We found our first flag.happy you.
To capture the second flag we need to understand what Oauth is.
We can see that am external website was able to authenticate us the app.That has to do with deep links.
So there most be an intimating request hardcoded to the app source code telling us what link to open let find that out.
By opening the manifest file we decompiled via APKtool we can see that we have two activities.
“com.hacker101.oauth.Browser” and “com.hacker101.oauth.MainActivity” 
We can see an intent filter on both activities.
The MainActivity is seen to contain a scheme(Read in resources file).
See image in the source directory.
Oauth://login.
Digging deep wwe can see in source code that the browser activity is called when authredirect variable is not null.We can see in the source code that the app also check for a redirect uri variable if not null change the value of Authredirect to the value of it intent filter url instead oauth://final.there we can come in and find a way to call the app with our own crafted intent.
Using the am command(check source code file)
We can call the app so it redirect to our website site we are evil lol.

We can also see in the Browser Activity code we have an exposed java script interface which we can create a  page to get it ( See payload.php).
Yaay our second flag.
NOTE:
ALWAYS TRY FIRST BEFORE ATTEMPTING THE EXPO
YOU MAY NOT FULLY UNDERSTAND THIS TUTORIAL BUT THE NUMBER OF ATTEMPS AND DETERMINATION WILL SURELY GIVE YOU THE FLAG(CHECK GOODGUY001) DASHBOARD
CHECK RESOURCES FILE FOR MORE INFO ON ITENT FILTERS AND REFRENCES.
CHECK IMAGE FILE FOR INDEPT UNDERSTANDING.
