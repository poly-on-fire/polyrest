*poly-on-fire* is a collection of proof-of-concept projects using [Polymer](https://www.polymer-project.org/) and [Firebase](https://firebase.google.com/)

|[**_Pete Carapetyan_**](http://appwriter.com)|  [TL;DR? blog](https://betterologist.net/2018/04/poly-on-fire-polymer-on-firebase/) |[TL;DR? _video:_](https://youtu.be/P9DwkqqUxNs)|
| --- | --- | --- |
|<a href="http://appwriter.com"><img class="style-svg" src="https://betterologist.net/wp-content/uploads/2016/05/pete-300x297.jpg" alt="pete" width="116" height="115" /></a>|<a href="https://betterologist.net/2018/04/poly-on-fire-polymer-on-firebase/" ><img class="style-svg" src="http://docs.datafundamentals.com/txt.png" alt="jammazwanPhotoSmall" width="200" height="116" /></a>|<a href="https://youtu.be/P9DwkqqUxNs"><img class="style-svg" src="https://betterologist.net/wp-content/uploads/2016/05/jamzVid1.png" alt="about" width="115" height="115" /></a>|


##### A project for learning an aspect of developing a Polymer app, deployed on Firebase hosting.

The idea is to prove out an approach or component in the simplest project first, before combining it with other code in a real project.

----

# \<polyrest\>

## What it does:

This is a kind of database client for HATEOAS-REST, much in the vein of phpAdmin or something like that for SQL dbs.

This video of the app working will probably explains it best: https://youtu.be/ydklb9T_8Bs

If you don't know HATEOAS then it still might not make much sense to you, and perhaps something such as this might begin to explain: https://docs.spring.io/spring-hateoas/docs/current/reference/html/

For more info, see the docs directory.

This was written in 2015 with Polymer 1 and a very minimal javascript skillset. Gosh only knows what you will find here.

It has never been deployed on firebase, but I keep it with my other polymer projects here in poly-on-fire, because it's part of my Polymer portfolio.
## PolyRest

The app itself is viewable and running at http://polyrest.datafundamentals.com
2 minute youtube demo at https://youtu.be/ydklb9T_8Bs

## To Run This Code:

This source code was originally designed to work with the full version of
PolymerStarterKit, but was reconfigured to work with the light version,
due to repeated NPM hangs on several occassions, months apart, and lasting 
for days at a time.
Friends don't let friends depend on NPM? Dunno. Not waiting around to find out.

To install and run this app, copy the following bash script to a location
 in your project folder, and run it. This will download everything you need,
  create a polyrest app and then run it as a python app as
  http://localhost:8080

You may have to answer Y/N to a few prompts on random .md files, but otherwise
 it should work on your local 'nix box without modification. (???). Tested on
 macosx and ubuntu, that's about it.

```
echo "About to create and run polyrest"
polydir=$1
if [ $# -eq 0 ]
  then echo "You did not specify a directory. Using polyrest";polydir="polyrest"
fi
mkdir $polydir
cd $polydir
curl -O http://docs.datafundamentals.com/lib/polymer-starter-kit-light-1.2.1.zip
ls
unzip polymer-starter-kit-light-1.2.1.zip
git clone https://github.com/datafundamentals/polyrest.git
rm -rf app/elements
rm -rf app/test/my*
rm app/index.html
rm app/styles/app*
mv -f polyrest/* app/
mv -f polyrest/.* app/
mv polyrest/styles/* app/styles
rm -rf __MACOSX
rm -rf polyrest
mv -f app polyrest
cd polyrest
python -m SimpleHTTPServer 8080
```
