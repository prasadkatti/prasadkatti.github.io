---
layout: post
title:  "Time tracking"
date:   2018-03-28 08:10:03 -0800
categories: hacking
---

I noticed today that I had [RescueTime](https://www.rescuetime.com/) installed on my mac. I must have installed it long back because I don't remember ever going to the dashboard to look at the reports.

So the way RescueTime works is you install a small application on your mac/PC and it sends information about how you spend your time to their servers in the cloud. With all the talk about privacy and given that I never even look at the dashboard, I decided to uninstall the application and delete my account. But I thought I would look at the dashboard one last time. The dashboard shows you which application you used and for how long. It also figures out which webpages you visited and how much time you spent on them.

I was curious about how all of this works. So I went through their [FAQs](https://www.rescuetime.com/faq) and they just get the information about the application running in the foreground. That got me curious on how one would go about programatically determining the application that is active. A simple google search took me to this SuperUser page - 
[how-do-i-tell-which-app-stole-my-focus-in-os-x](https://superuser.com/questions/734007/how-do-i-tell-which-app-stole-my-focus-in-os-x)

This snippet will print the app which has focus at one second intervals. 

{% highlight python %}
#!/usr/bin/python                                                                                                       

from time import sleep
from AppKit import NSWorkspace

while True:
    app = NSWorkspace.sharedWorkspace().activeApplication()
    print (app['NSApplicationName'])
    sleep(1)
{% endhighlight %}

Demo -

<script src="https://asciinema.org/a/C53JeN00DKZoU5P48Oiz64gop.js" id="asciicast-C53JeN00DKZoU5P48Oiz64gop" async></script>
