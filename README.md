
## Hastie - Static Site Generator in Go

Started: Feb 13, 2012

Hastie is intended as replacement of jekyll (for myself), but jekyll has a 
robust plugin, extensibility and community that I do not expect to even attempt.
If you are looking for a flexible tool to publish your site use jekyll.

If you are looking for a tool to tweek and play with the Go language, then this
might be your choice. Most customizations will probably require code changes.
The reason I created the tool was to learn Go, I'm publishing to hopefully 
help others with playing with the language.

Note: The name Hastie also comes from the novel Dr. Jekyll and Mr. Hyde

--------------------------------------------------------------------------------

## Install Notes

You need Go binaries already installed see: http://golang.org/doc/install.html

For my Mac I use homebrew, so it was simply a matter of: `brew install go`

For my Linux environments I use a Debian variant so you can install with: `apt-get install golang`


Uses blackfriday for markdown conversion. 
Install:
  $ goinstall github.com/russross/blackfriday

Users goconf for reading configuration file
Install:
  $ goinstall goconf.googlecode.com/hg

  If the above does not work, try
  $ cd $GOROOT/src/pkg/goconf/googlecode.com/hg
  $ gomake install


--------------------------------------------------------------------------------

## Usage

Hastie walks through a templates directory and generates HTML files to a publish 
directory. It uses Go's template language for templates and markdown for content.

Here is sample site layout: (see test directory)

    layouts/footer.html
    layouts/header.html
    layouts/indexpage.html
    layouts/post.html
    posts/2011-03-02-angelica.html
    posts/index.md
    posts/zebra/2009-12-12-sample-post.md
    posts/zebra/2012-02-14-hastie-intro.md


This will generate:

    public/angelica.html
    public/index.html
    public/zebra/sample-post.html
    public/zebra/hastie-intro.html


A few current limitations:
  - all files must be have .md extension
  - sub-directories are only one level deep


The usage of hastie is just as a template engine, it does not copy over
and images, have a built-in web server or any of the other features that
jekyll has.

I keep the `public` directory full with all of the assets for the site such 
as images, stylesheets, etc and hastie copies in the html files. So if you 
delete a template it won't be removed from `public`


Data available to templates:

    .Title
    .Date
    .Content
    .Category
    .OutFile -- file path
    .Recent -- list of 3 most recent files
    .Pages -- list of all page obhects


--------------------------------------------------------------------------------


### TODO

* Recent Files: Create List of Recent Files by Category

* Create Next-Prev Links by Category
* Create LESS converter for stylesheets
* Read .html files and apply template, no markdown
* Add ability to support rss.xml

* Command Line Arguments
* --verbose : --help
