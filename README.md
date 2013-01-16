Weinre on OpenShift
=========================

weinre is WEb INspector REmote. Pronounced like the word "winery". Or maybe like the word "weiner". Who knows, really.

weinre is a debugger for web pages, like FireBug (for FireFox) and Web Inspector (for WebKit-based browsers), except it's designed to work remotely, and in particular, to allow you debug web pages on a mobile device such as a phone.

Running on OpenShift
--------------------

Create an account at http://openshift.redhat.com/

Create a weinre application

    rhc app create -a weinre -t diy-0.1

Add this upstream weinre repo

    cd weinre
    git remote add upstream -m master git://github.com/openshift/weinre-quickstart.git
    git pull -s recursive -X theirs upstream master

Then push the repo top OpenShift

    git push

That's it, you can now checkout your application at:

    http://weinre-$namespace.rhcloud.com


Repo layout
===========
weinre.server/ - A build of weinre
.openshift/action_hooks/start - Script that gets run to start weinre and direct console output to the log 
.openshift/action_hooks/stop - Script that gets run to stop weinre

