# BodyMatcher

BodyMatcher simplifies your view testing.  Forget assert_select.

## Activate it by including it in your Test::Unit::TestCase class:

	class Test::Unit::TestCase
	    include BodyMatcher

	    self.use_transactional_fixtures = true
	    self.use_instantiated_fixtures  = false
	end

## Simple assertions:

	 body_matcher['#web_results'].should.match /results from the web/i

	 body_matcher['#categories_dropdown'].should.include "#{topic}[#{count}]" 

## Access the attributes:

	 body_matcher['#name_field'].attributes['value'].should.equal '(your name)'
	 body_matcher['#name_field']['value'].should.equal '(your name)'

The nice part about this is that test failures will print out only
the HTML you're trying to match.

For use with test/spec/rails, which provides the 'body' method.  Also 
requires Hpricot. Enjoy.
 
## Credits

* Chris Wanstrath [ chris@ozmm.org ]
* Updated by Bobby Uhlenbrock

## Change Log

**06.27.2008** Modified for compatibility with test/spec 0.4.0.
Removed the body alias_method and added a new body_matcher method 
to traverse @response.body.