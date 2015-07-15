Quick Start
===========

If your database follows the schema the plugin expects to work with you can simply kick start your users in the application by just adding the component and helper. This tutorial is the minimalistic implementation and will use the component and helper with their default settings. For customization of the default behavior check the documentation or read the code of the settings arrays.

In src\Controller\UsersController.php:

```php
namespace App\Controller;

use App\Controller\AppController;
use Cake\Event\Event;

class UsersController extends AppController {
	public function initialize() {
		parent::initialize();
		$this->loadComponent('Burzum/UserTools.UserTool');
	}

	// To use the helper you'll have to set the user data to the view!
	public function beforeRender(Event $event) {
		$this->set('userData', $this->Auth->user());
	}
}
```

In src\View\AppView.php:

```php
namespace App\View;

use App\View\View;

class AppView extends View {
	public function initialize() {
		parent::initialize();
		$this->loadHelper('Burzum/UserTools.Auth');
	}
}
```

The component will take the main model of the controller and load the [UserBehavior](../Documentation/The-User-Behavior.md) with it's default settings.

Go to ```/users/register``` and try to register, make sure your email config is set up properly.

You should receive an email notification with a token and a verification URL. After verifying your user go to ```/users/login``` and try to login.
