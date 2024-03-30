# SafeLoan Contract

O contrato SafeLoan é um contrato inteligente que permite aos usuários emprestar tokens ERC20 com base em garantias de colateral. Este contrato é útil em casos em que um usuário precisa de liquidez instantânea sem vender seus ativos criptográficos.

## Funcionalidades

- Os usuários podem solicitar empréstimos especificando a quantidade desejada a ser emprestada e a quantidade de colateral que estão dispostos a fornecer.
- O contrato verifica se a proporção entre o valor do empréstimo e o valor do colateral atende ao mínimo exigido.
- Uma vez que o empréstimo é concedido, os fundos são transferidos para o mutuário, e o colateral é mantido no contrato até que o empréstimo seja pago.
- Os usuários podem reembolsar seus empréstimos a qualquer momento, adicionando juros acumulados com base em uma taxa de juros anual definida.

## Parâmetros

- `collateralToken`: O token ERC20 usado como colateral para os empréstimos.
- `interestRate`: A taxa de juros anual aplicada aos empréstimos.
- `minCollateralizationRatio`: A proporção mínima entre o valor do empréstimo e o valor do colateral exigido.

## Eventos

- `LoanGranted`: Emitido quando um empréstimo é concedido. Contém informações sobre o mutuário, o valor emprestado e a quantidade de colateral fornecida.
- `LoanRepaid`: Emitido quando um empréstimo é reembolsado. Contém informações sobre o mutuário, o valor do empréstimo e a quantidade reembolsada.

## Como usar

1. Deploy do contrato SafeLoan com os parâmetros desejados.
2. Os usuários podem solicitar empréstimos chamando a função `requestLoan`, especificando a quantidade desejada a ser emprestada e a quantidade de colateral que estão dispostos a fornecer.
3. Após a concessão do empréstimo, os fundos serão transferidos para o mutuário, e o colateral será bloqueado no contrato.
4. Os usuários podem reembolsar seus empréstimos a qualquer momento chamando a função `repayLoan`.

## Exemplo de Uso

```solidity
// Deploy do contrato SafeLoan
SafeLoan safeLoan = new SafeLoan(collateralTokenAddress, interestRate, minCollateralizationRatio);

// Solicitar um empréstimo
safeLoan.requestLoan(borrowedAmount, collateralAmount);

// Reembolsar o empréstimo
safeLoan.repayLoan{value: repaidAmount}();
```

Certifique-se de substituir `collateralTokenAddress`, `interestRate`, `minCollateralizationRatio`, `borrowedAmount`, `collateralAmount` e `repaidAmount` pelos valores apropriados.
