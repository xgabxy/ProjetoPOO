MODEL - CLIENTE

package com.loja.model;

public class Cliente {
    private String nome;
    private String endereco;
    private String telefone;
    private String email;

    public Cliente(String nome, String endereco, String telefone, String email) {
        this.nome = nome;
        this.endereco = endereco;
        this.telefone = telefone;
        this.email = email;
    }

    @Override
    public String toString() {
        return "Nome completo: " + nome + ", Endereço: " + endereco + ", Telefone: " + telefone + ", E-mail: " + email;
    }
}


MODEL - PRODUTO

package com.loja.model;

public class Produto {
    private String nome;
    private String marca;
    private String preco;
    private String categoria;
    private String garantia;

    public Produto(String nome, String marca, String preco, String categoria, String garantia) {
        this.nome = nome;
        this.marca = marca;
        this.preco = preco;
        this.categoria = categoria;
        this.garantia = garantia;
    }

    @Override
    public String toString() {
        return "Nome: " + nome + ", Marca: " + marca + ", Preço: " + preco + ", Categoria: " + categoria + ", Garantia: " + garantia;
    }
}


MODEL - SERVICO

package com.loja.model;

public class Servico {
    private String nome;
    private String descricao;
    private String preco;

    public Servico(String nome, String descricao, String preco) {
        this.nome = nome;
        this.descricao = descricao;
        this.preco = preco;
    }

    @Override
    public String toString() {
        return "Nome: " + nome + ", Descrição: " + descricao + ", Preço: " + preco;
    }
}


MODEL - USUARIO

package com.loja.model;

public class Usuario {
    private String username;
    private String password;
    private String email;

    public Usuario(String username, String password, String email) {
        this.username = username;
        this.password = password;
        this.email = email;
    }

    public String getUsername() {
        return username;
    }

    public String getPassword() {
        return password;
    }

    public String getEmail() {
        return email;
    }
}


VIEW - CADASTROCLIENTE

package com.loja.view;

import com.loja.model.Cliente;

import javax.swing.*;
import java.awt.*;
import java.awt.event.ActionEvent;
import java.awt.event.ActionListener;
import java.util.ArrayList;
import java.util.List;

public class CadastroClientes extends JFrame {
    private JTextField nomeField, enderecoField, telefoneField, emailField;
    private JButton cadastrarButton, listarButton;
    private JTextArea outputArea;
    private List<Cliente> clientes;

    public CadastroClientes() {
        clientes = new ArrayList<>();
        nomeField = new JTextField(20);
        enderecoField = new JTextField(20);
        telefoneField = new JTextField(20);
        emailField = new JTextField(20);
        cadastrarButton = new JButton("Cadastrar");
        listarButton = new JButton("Listar");
        outputArea = new JTextArea(10, 40);
        outputArea.setEditable(false);

        JPanel inputPanel = new JPanel(new GridLayout(5, 2));
        inputPanel.add(new JLabel("Nome completo:"));
        inputPanel.add(nomeField);
        inputPanel.add(new JLabel("Endereço:"));
        inputPanel.add(enderecoField);
        inputPanel.add(new JLabel("Telefone:"));
        inputPanel.add(telefoneField);
        inputPanel.add(new JLabel("E-mail:"));
        inputPanel.add(emailField);
        inputPanel.add(cadastrarButton);
        inputPanel.add(listarButton);

        JPanel outputPanel = new JPanel();
        outputPanel.add(new JLabel("Clientes cadastrados:"));
        outputPanel.add(new JScrollPane(outputArea));

        add(inputPanel, BorderLayout.NORTH);
        add(outputPanel, BorderLayout.CENTER);

        cadastrarButton.addActionListener(new ActionListener() {
            public void actionPerformed(ActionEvent e) {
                cadastrarCliente();
            }
        });

        listarButton.addActionListener(new ActionListener() {
            public void actionPerformed(ActionEvent e) {
                listarClientes();
            }
        });

        setTitle("Cadastro de Cliente");
        pack();
        setDefaultCloseOperation(JFrame.DISPOSE_ON_CLOSE);
        setLocationRelativeTo(null);
        setVisible(true);
    }

    private void cadastrarCliente() {
        String nome = nomeField.getText();
        String endereco = enderecoField.getText();
        String telefone = telefoneField.getText();
        String email = emailField.getText();

        Cliente cliente = new Cliente(nome, endereco, telefone, email);
        clientes.add(cliente);
        outputArea.append(cliente.toString() + "\n");

        // Limpar campos após o cadastro
        nomeField.setText("");
        enderecoField.setText("");
        telefoneField.setText("");
        emailField.setText("");
    }

    private void listarClientes() {
        outputArea.setText("");
        for (Cliente cliente : clientes) {
            outputArea.append(cliente.toString() + "\n");
        }
    }
}


VIEW - CADASTRO PRODUTO

package com.loja.view;

import com.loja.model.Produto;

import javax.swing.*;
import java.awt.*;
import java.awt.event.ActionEvent;
import java.awt.event.ActionListener;
import java.util.ArrayList;
import java.util.List;

public class CadastroProduto extends JFrame {
    private JTextField nomeField, marcaField, precoField, categoriaField, garantiaField;
    private JButton cadastrarButton, listarButton;
    private JTextArea outputArea;
    private List<Produto> produtos;

    public CadastroProduto() {
        produtos = new ArrayList<>();
        nomeField = new JTextField(20);
        marcaField = new JTextField(20);
        precoField = new JTextField(20);
        categoriaField = new JTextField(20);
        garantiaField = new JTextField(20);

        cadastrarButton = new JButton("Cadastrar");
        listarButton = new JButton("Listar");
        outputArea = new JTextArea(10, 40);
        outputArea.setEditable(false);

        JPanel inputPanel = new JPanel(new GridLayout(6, 2));
        inputPanel.add(new JLabel("Nome:"));
        inputPanel.add(nomeField);
        inputPanel.add(new JLabel("Marca:"));
        inputPanel.add(marcaField);
        inputPanel.add(new JLabel("Preço:"));
        inputPanel.add(precoField);
        inputPanel.add(new JLabel("Categoria:"));
        inputPanel.add(categoriaField);
        inputPanel.add(new JLabel("Garantia:"));
        inputPanel.add(garantiaField);
        inputPanel.add(cadastrarButton);
        inputPanel.add(listarButton);

        JPanel outputPanel = new JPanel();
        outputPanel.add(new JLabel("Cadastro de Produtos de Informática:"));
        outputPanel.add(new JScrollPane(outputArea));

        add(inputPanel, BorderLayout.NORTH);
        add(outputPanel, BorderLayout.CENTER);

        cadastrarButton.addActionListener(new ActionListener() {
            public void actionPerformed(ActionEvent e) {
                cadastrarProduto();
            }
        });

        listarButton.addActionListener(new ActionListener() {
            public void actionPerformed(ActionEvent e) {
                listarProdutos();
            }
        });

        setTitle("Cadastro de Produtos de Informática");
        pack();
        setDefaultCloseOperation(JFrame.DISPOSE_ON_CLOSE);
        setLocationRelativeTo(null);
        setVisible(true);
    }

    private void cadastrarProduto() {
        String nome = nomeField.getText();
        String marca = marcaField.getText();
        String preco = precoField.getText();
        String categoria = categoriaField.getText();
        String garantia = garantiaField.getText();

        Produto produto = new Produto(nome, marca, preco, categoria, garantia);
        produtos.add(produto);
        outputArea.append(produto.toString() + "\n");

        // Limpar campos após o cadastro
        nomeField.setText("");
        marcaField.setText("");
        precoField.setText("");
        categoriaField.setText("");
        garantiaField.setText("");
    }

    private void listarProdutos() {
        outputArea.setText("");
        for (Produto produto : produtos) {
            outputArea.append(produto.toString() + "\n");
        }
    }
}


VIEW - CADASTROSERVICO

package com.loja.view;

import com.loja.model.Servico;

import javax.swing.*;
import java.awt.*;
import java.awt.event.ActionEvent;
import java.awt.event.ActionListener;
import java.util.ArrayList;
import java.util.List;

public class CadastroServico extends JFrame {
    private JTextField nomeField, descricaoField, precoField;
    private JButton cadastrarButton, listarButton;
    private JTextArea outputArea;
    private List<Servico> servicos;

    public CadastroServico() {
        servicos = new ArrayList<>();
        nomeField = new JTextField(20);
        descricaoField = new JTextField(20);
        precoField = new JTextField(20);

        cadastrarButton = new JButton("Cadastrar");
        listarButton = new JButton("Listar");
        outputArea = new JTextArea(10, 40);
        outputArea.setEditable(false);

        JPanel inputPanel = new JPanel(new GridLayout(4, 2));
        inputPanel.add(new JLabel("Nome:"));
        inputPanel.add(nomeField);
        inputPanel.add(new JLabel("Serviço:"));
        inputPanel.add(descricaoField);
        inputPanel.add(new JLabel("Preço:"));
        inputPanel.add(precoField);
        inputPanel.add(cadastrarButton);
        inputPanel.add(listarButton);

        JPanel outputPanel = new JPanel();
        outputPanel.add(new JLabel("Cadastro de Serviços de Informática:"));
        outputPanel.add(new JScrollPane(outputArea));

        add(inputPanel, BorderLayout.NORTH);
        add(outputPanel, BorderLayout.CENTER);

        cadastrarButton.addActionListener(new ActionListener() {
            public void actionPerformed(ActionEvent e) {
                cadastrarServico();
            }
        });

        listarButton.addActionListener(new ActionListener() {
            public void actionPerformed(ActionEvent e) {
                listarServicos();
            }
        });

        setTitle("Cadastro de Serviços de Informática");
        pack();
        setDefaultCloseOperation(JFrame.DISPOSE_ON_CLOSE);
        setLocationRelativeTo(null);
        setVisible(true);
    }

    private void cadastrarServico() {
        String nome = nomeField.getText();
        String descricao = descricaoField.getText();
        String preco = precoField.getText();

        Servico servico = new Servico(nome, descricao, preco);
        servicos.add(servico);
        outputArea.append(servico.toString() + "\n");

        // Limpar campos após o cadastro
        nomeField.setText("");
        descricaoField.setText("");
        precoField.setText("");
    }

    private void listarServicos() {
        outputArea.setText("");
        for (Servico servico : servicos) {
            outputArea.append(servico.toString() + "\n");
        }
    }
}


VIEW - CADASTROUSUARIO

package com.loja.view;

import com.loja.model.Usuario;

import javax.swing.*;
import java.awt.*;
import java.awt.event.ActionEvent;
import java.awt.event.ActionListener;
import java.util.regex.Matcher;
import java.util.regex.Pattern;

public class CadastroUsuario extends JFrame {
    private JTextField usernameField, emailField;
    private JPasswordField passwordField, confirmPasswordField;
    private JButton registerButton;

    public CadastroUsuario() {
        setTitle("Cadastro de Usuário - LOJA DO PRIMO");
        setSize(300, 250);
        setDefaultCloseOperation(JFrame.DISPOSE_ON_CLOSE);
        setLocationRelativeTo(null);

        JPanel panel = new JPanel(new GridLayout(5, 2));
        usernameField = new JTextField();
        emailField = new JTextField();
        passwordField = new JPasswordField();
        confirmPasswordField = new JPasswordField();
        registerButton = new JButton("Registrar");

        panel.add(new JLabel("Username:"));
        panel.add(usernameField);
        panel.add(new JLabel("Email:"));
        panel.add(emailField);
        panel.add(new JLabel("Password:"));
        panel.add(passwordField);
        panel.add(new JLabel("Confirm Password:"));
        panel.add(confirmPasswordField);
        panel.add(new JLabel());
        panel.add(registerButton);

        add(panel);

        registerButton.addActionListener(new ActionListener() {
            @Override
            public void actionPerformed(ActionEvent e) {
                String username = usernameField.getText();
                String email = emailField.getText();
                String password = new String(passwordField.getPassword());
                String confirmPassword = new String(confirmPasswordField.getPassword());

                if (!isValidUsername(username)) {
                    JOptionPane.showMessageDialog(CadastroUsuario.this, "O nome de usuário deve ter no máximo 20 caracteres e conter apenas letras e números.");
                    return;
                }

                if (!isValidEmail(email)) {
                    JOptionPane.showMessageDialog(CadastroUsuario.this, "Por favor, insira um e-mail válido.");
                    return;
                }

                if (password.isEmpty() || confirmPassword.isEmpty()) {
                    JOptionPane.showMessageDialog(CadastroUsuario.this, "Todos os campos são obrigatórios.");
                    return;
                }

                if (password.length() < 8) {
                    JOptionPane.showMessageDialog(CadastroUsuario.this, "A senha deve ter no mínimo 8 caracteres.");
                    return;
                }

                if (!password.equals(confirmPassword)) {
                    JOptionPane.showMessageDialog(CadastroUsuario.this, "As senhas não conferem. Tente novamente.");
                    return;
                }

                LoginView.addUsuario(new Usuario(username, password, email));
                JOptionPane.showMessageDialog(CadastroUsuario.this, "Usuário registrado com sucesso!");
                dispose();
            }
        });

        setVisible(true);
    }

    private boolean isValidUsername(String username) {
        if (username.length() > 20) {
            return false;
        }
        String regex = "^[a-zA-Z0-9]+$";
        Pattern pattern = Pattern.compile(regex);
        Matcher matcher = pattern.matcher(username);
        return matcher.matches();
    }

    private boolean isValidEmail(String email) {
        String regex = "^[\\w-\\.]+@([\\w-]+\\.)+[\\w-]{2,4}$";
        Pattern pattern = Pattern.compile(regex);
        Matcher matcher = pattern.matcher(email);
        return matcher.matches();
    }
}


VIEW - LOGINVIEW

package com.loja.view;

import com.loja.model.Usuario;

import javax.swing.*;
import java.awt.*;
import java.awt.event.ActionEvent;
import java.awt.event.ActionListener;
import java.util.ArrayList;
import java.util.List;

public class LoginView extends JFrame {
    private JTextField usernameField;
    private JPasswordField passwordField;
    private JButton loginButton, registerButton;
    private static List<Usuario> usuarios = new ArrayList<>();

    public LoginView() {
        // Configurações da janela de login
        setTitle("Login - LOJA DO PRIMO");
        setSize(300, 200);
        setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        setLocationRelativeTo(null);

        // Componentes da interface
        JPanel panel = new JPanel(new GridLayout(4, 2));
        usernameField = new JTextField();
        passwordField = new JPasswordField();
        loginButton = new JButton("Login");
        registerButton = new JButton("Cadastre-se");

        panel.add(new JLabel("Username:"));
        panel.add(usernameField);
        panel.add(new JLabel("Password:"));
        panel.add(passwordField);
        panel.add(loginButton);
        panel.add(registerButton);

        add(panel);

        loginButton.addActionListener(new ActionListener() {
            @Override
            public void actionPerformed(ActionEvent e) {
                String username = usernameField.getText();
                String password = new String(passwordField.getPassword());

                // Verificar se o usuário existe
                if (authenticate(username, password)) {
                    dispose();
                    new MenuView();
                } else {
                    JOptionPane.showMessageDialog(LoginView.this, "Usuário ou senha inválidos");
                }
            }
        });

        registerButton.addActionListener(new ActionListener() {
            @Override
            public void actionPerformed(ActionEvent e) {
                new CadastroUsuario();
            }
        });

        setVisible(true);
    }

    private boolean authenticate(String username, String password) {
        for (Usuario usuario : usuarios) {
            if (usuario.getUsername().equals(username) && usuario.getPassword().equals(password)) {
                return true;
            }
        }
        return false;
    }

    public static void addUsuario(Usuario usuario) {
        usuarios.add(usuario);
    }
}


VIEW - MENUVIEW

package com.loja.view;

import javax.swing.*;
import java.awt.event.ActionEvent;
import java.awt.event.ActionListener;

public class MenuView extends JFrame {
    private JButton cadastroClienteButton;
    private JButton cadastroProdutoButton;
    private JButton cadastroServicoButton;

    public MenuView() {
        setTitle("Menu Principal - LOJA DO PRIMO");
        setSize(400, 200);
        setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        setLocationRelativeTo(null);

        JPanel panel = new JPanel();
        cadastroClienteButton = new JButton("Cadastro de Clientes");
        cadastroProdutoButton = new JButton("Cadastro de Produtos");
        cadastroServicoButton = new JButton("Cadastro de Serviços");

        panel.add(cadastroClienteButton);
        panel.add(cadastroProdutoButton);
        panel.add(cadastroServicoButton);

        add(panel);

        cadastroClienteButton.addActionListener(new ActionListener() {
            @Override
            public void actionPerformed(ActionEvent e) {
                new CadastroClientes();
            }
        });

        cadastroProdutoButton.addActionListener(new ActionListener() {
            @Override
            public void actionPerformed(ActionEvent e) {
                new CadastroProduto();
            }
        });

        cadastroServicoButton.addActionListener(new ActionListener() {
            @Override
            public void actionPerformed(ActionEvent e) {
                new CadastroServico();
            }
        });

        setVisible(true);
    }
}


VIEW - MAIN 

package com.loja.view;

public class Main {
    public static void main(String[] args) {
        new LoginView();
    }
}
