# State Machine

    var StateMachine = require('state_machine');

    var sm = new StateMachine({
      state: 'q0',
      acceptingStates: ['q3'],
      transitions: {
        'q0': {
          'a':'q1',
          '*':'q2'},
        'q2': {
          'z': 'q3'
        }
      }
    });

    // transition to a new state
    sm.transition('b');
    // the special '*' catch-all input moves the state machine to q2
    sm.state
    => 'q2'

    sm.accept()
    => false
    q2.transition('z')
    sm.accept()
    => true

    var dfn = sm.definition();
    // can be serialized for later restoration...

    var sm_ = new StateMachine(dfn);